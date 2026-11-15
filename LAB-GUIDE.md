# Lab guide: PIM and access reviews

**Time:** 40 min, plus a short wait. **Cost:** free with the P2 trial.
**Skills:** just in time access, approval and MFA on elevation, audit trails, access reviews, compliance evidence.

Uses Jordan Lee and `rg-lakeview-dev` from the RBAC lab. 📸 = screenshot. Redact IDs and names in exports.

## Before you start

**Accounts and licenses**
- [ ] **Lakeview Health tenant and subscription**, with Jordan Lee and `rg-lakeview-dev` from the RBAC lab.
- [ ] **Microsoft Entra ID P2 trial** (Step 1 starts it; free for 30 days. If Microsoft asks for a card, it's to verify you; set a reminder to cancel before day 30).
- [ ] **Jordan's Authenticator** already set up from the RBAC lab (PIM activation asks for MFA).

**Software:** none. Use a normal window for your admin account and a **private window** for Jordan.

## License (5 min)

**1.** Entra admin > Identity Governance > Privileged Identity Management. If asked, start the free **Microsoft Entra ID P2** trial. Assign P2 to yourself and Jordan (Users > user > Licenses).
*Why:* PIM and access reviews are P2 features. The trial lasts 30 days.

## Just in time access (20 min)

**2. Eligible, not permanent.** PIM > Azure resources > `rg-lakeview-dev` > Assignments > Add assignments > **Contributor** > Jordan > type **Eligible** > 30 days. 📸

**3. Rules for activation.** PIM > Azure resources > `rg-lakeview-dev` > Settings > Contributor > Edit: max **1 hour**, **require justification**, **require MFA**. Save.
*Why:* no standing admin rights. Every elevation has a reason, a time limit and MFA.

**4. Activate as Jordan.** Private window > PIM > My roles > Azure resources > Activate > reason "Deploy test app". 📸 the active assignment with its end time.

**5. Audit trail.** As yourself: PIM > Azure resources > `rg-lakeview-dev` > Resource audit. 📸 the activation record.

## Access review (15 min)

**6. Group and review.** Create group `Lakeview-Developers` with Jordan and one other test user. Identity Governance > Access reviews > New access review > Teams + Groups > `Lakeview-Developers` > reviewer: **you** > 1 day > **Auto apply results** on, **If reviewers don't respond: Remove access** > Create.

**7. Decide.** myaccess.microsoft.com > Access reviews > approve Jordan with a reason, deny the other user. Back in the review: **Stop** > **Apply**. The denied user leaves the group. 📸 the results.
*Why:* access that nobody vouches for gets removed automatically. That's what SOX and SOC 2 auditors check.

**8. Evidence.** Download the review results and the PIM audit, redact names, and save them in `evidence/` as `*-redacted.csv`. Fill in the README.
