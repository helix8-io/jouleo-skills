# Examples

## Contents
- Daily review reply
- Email to enquiry
- Risky action waiting for a yes

## Daily review reply

The person asks: "What needs doing today?" After `jouleo_today`, reply in this shape — urgent first, at most five actions, links kept:

```markdown
**Today in Jouleo**

1. **Overdue:** survey report for the Hughes job was due Tue 6 Oct — [open job](https://acme.jouleo.co.uk/jobs/job-1a2b)
2. **Install Thu 9 Oct** (2 days) at the Patel job — no team set yet. Want me to add Sam and Ali?
3. **Critical flag:** G98 notification missing on the Owens job — [open job](https://acme.jouleo.co.uk/jobs/job-3c4d)
4. **2 drafts** waiting for your approval in Approvals.
5. **3 jobs** with no survey date — want me to suggest dates?
```

Keep it to what changes the person's day. Don't repeat jobs that need nothing.

## Email to enquiry

The person pastes:

> Hi, we're looking at solar panels for our house, 14 Mill Lane, Larne. It's a detached 1990s house with a concrete tiled roof facing south. Probably about 4kW. Call me on 07700 900456. — Rachel Moore

1. `jouleo_enquiry_form` → this company asks for jobType, customerName, addressLine, town, postcode, contact, technologyType, systemSizeRequested, mountingType, propertyTypeResidential, propertyConstruction, propertyAge, roofCovering, shadingAtEnquiry.
2. `jouleo_find_address` with "14 Mill Lane, Larne", then the chosen addressId → addressLine, town, postcode.
3. Map what the email answers:

```json
{
  "jobType": "Residential",
  "customerName": "Rachel Moore",
  "addressLine": "14 Mill Lane",
  "town": "Larne",
  "postcode": "BT40 1AB",
  "contact": "07700 900456",
  "technologyType": "Solar PV",
  "systemSizeRequested": "4",
  "mountingType": "Roof mounted",
  "propertyTypeResidential": "Detached",
  "propertyAge": "1990s",
  "roofCovering": "Concrete interlocking tile"
}
```

4. Still missing and required: propertyConstruction and shadingAtEnquiry. Ask once: "Two things before I add it: is the house cavity wall or solid brick, and is there any shading on the roof?" — or, if the person wants it added now, use "Not yet assessed" for shading only if the form offers it.
5. `jouleo_add_enquiry` → reply with the job link.

The postcode comes from the address lookup, never from memory.

## Risky action waiting for a yes

The person says: "Archive the Moore job, they went with someone else."

1. `jouleo_find_jobs` → the job id.
2. `jouleo_archive_job` with `reason: "lost_to_competitor"` → the reply is a preview and a confirmationId. Nothing has changed.
3. Show the preview in plain words and stop:

> I'll archive the Moore job (14 Mill Lane, Larne) as **lost to a competitor**. Shall I go ahead?

4. Only after a clear yes, call `jouleo_archive_job` again with the same arguments and the confirmationId.

If the person says anything other than a clear yes, don't confirm.
