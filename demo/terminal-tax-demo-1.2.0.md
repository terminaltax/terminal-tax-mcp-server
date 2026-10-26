# Terminal Tax demo 1.2.0: transcript

[terminal-tax-demo-1.2.0.mp4](terminal-tax-demo-1.2.0.mp4) (3 min 58 s, no audio), recorded 2026-10-26 on the Terminal Tax test site (app.terminal.tax) with a fictional taxpayer, Casey Rivera. Nothing was sent to the IRS and no card was charged.

The chat is a real session, replayed: an AI agent (Claude Code, run headless, with nothing installed or connected) talking with a simulated customer who answers its questions in plain words and shares a W-2 and a 1099-INT as PDF files. The customer names Terminal Tax and the agent reaches it by itself with ordinary web requests. The assistant's words are its own and are shown unedited, except that the filing link is shortened and one note is added (below). The filing page part shows a fresh filing link made from a prepared return with the same facts (the chat's own link was used up by an earlier recording attempt). What the assistant says Terminal Tax covers describes the service on the recording date; the current scope is at https://terminal.tax/llms.txt.

## Title card

Filing taxes from a chat. A taxpayer talks with their own AI assistant, then reviews, signs and pays on one Terminal Tax page. Test site with a synthetic taxpayer: nothing is sent to the IRS and no card is charged.

## The chat

**Customer:** hey! can you help me file a tax return with terminal tax? i'm trying their test site, app.terminal.tax, with a made-up test taxpayer they gave me, so nothing actually gets filed

**Assistant:**

I'll take a look at the site first to see how it works.

*Terminal Tax: Read the instructions for agents*

**Assistant:**

I can help, but there's a problem to sort out before I send anything. **Their docs don't describe a test site.**

I read the homepage and the developer guide (`app.terminal.tax/llms.txt`):

- **No test mode is documented.** There's no sandbox, staging host, or test flag. The only endpoint is `https://app.terminal.tax/v1/hosted-mcp`, and the site describes it as live e-filing with real IRS submission and a $19.99 fee once the IRS accepts the return.
- **How it works:** I'd open a session, get the form layout they expect, and send the tax figures and identity details (name, date of birth, address, bank account, and so on). They'd send back a private link. You'd open it, enter the SSN and PINs yourself, review, sign, and pay. Nothing goes to the IRS until you sign on that page.

So there's a gap between what you were told and what the site says. If it really is production, signing a return for a made-up taxpayer would send a fake return to the IRS. I don't want to help with that by accident.

How we could go from here:

1. **Check with whoever gave you the test taxpayer**, or email support@terminal.tax, to ask whether there's a separate test host or mode. They may have one that isn't in the public docs.
2. **Go part of the way:** I can do every step up to getting the filing link back, which would test the setup without filing. Your fake data would still be sent to and stored on their real server, though they say they erase it if you decline or the link expires. **Don't sign on the hosted page.**

If you want option 2, or you confirm a test host, send me the test taxpayer's details: the W-2/1099 figures, filing status, name, address, date of birth, and dependents. Leave out the SSN, since that only goes on their page.

*Note added for this video: app.terminal.tax is Terminal Tax's test site. It accepts only test identities like Casey's, sends nothing to the IRS and charges no card.*

**Customer:** terminal tax told me app.terminal.tax is their test site, and it only accepts their made-up test taxpayers and never files with the irs. i'd still like to go ahead, so can you keep going and get me the link?

**Assistant:**

Got it. I'll start the session and get the schema. I still need the test taxpayer's details to fill it in.

*Terminal Tax: Read the instructions for agents*

*Terminal Tax: Opened a filing session*

*Terminal Tax: Read the return format*

**Assistant:**

The session file got cut off when I saved it, so I'll reuse the handle from the output above.

*Terminal Tax: Read the return format*

**Assistant:**

Thanks for checking with them. I've opened a filing session and downloaded the form layout. Nothing has been sent about any taxpayer yet. The session was empty and carries no tax data.

To go further I need the test taxpayer's details. The service only accepts facts you give me, and I shouldn't make any up, even for a fake person. Please paste whatever Terminal Tax gave you, ideally the test W-2 and any 1099s plus:

1. **Identity:** legal name, date of birth, mailing address, occupation, email and mobile number
2. **Filing status:** single, married filing jointly, or head of household. For a joint return, the spouse's name, date of birth and occupation too
3. **Last year:** did they file a 2024 return, and if so, the 2024 AGI (adjusted gross income)
4. **Forms:** the box amounts from each W-2 or 1099, including the employer or payer name, EIN and address
5. **Yes/no facts:**
   - Is this an original return or an amended one?
   - Were they a U.S. citizen or resident all year?
   - Are they blind?
   - Were they born before January 2, 1961?
   - Can anyone claim them as a dependent?
   - Any digital assets?
   - Any dependents?
6. **Refund or balance due:** paper check, or a bank account for direct deposit (a test routing and account number)

Leave out the SSN and any PINs. Those only go on the filing page.

Once I have these, I'll match them to the closest starter form (for example "single, one W-2, refund"), fill it in, and send it. I'll ask you about anything it flags as missing, then give you the link.

One more thing: the public docs don't mention a test mode at all. Before you sign on that page, check that it clearly shows it's a test environment.

**Customer:** here's my W-2 and the credit union 1099-INT, it's tiny. i'm casey rivera, born july 14 1996, single, no dependents, shift lead at a coffee roastery, 88 W 5th Ave Apt 3 Columbus OH 43201. email is casey.rivera@checks.terminal.tax, i'd rather not give a phone number, refund by paper check, 2024 AGI was 43910, and none of the other stuff applies to me.
[ATTACH lakeside-1099-int-2025.pdf] *(attaches casey-w2-2025.pdf)*

*Read casey-w2-2025.pdf*

*Read lakeside-1099-int-2025.pdf*

**Assistant:**

Both forms look clearly like test data (EIN 12-3456789, a 555 phone number). I'll get the matching starter template, "single, one W-2 and one 1099-INT, refund".

*Terminal Tax: Read the return format*

**Assistant:**

I've read both forms and have the matching starter template ("single, one W-2 and one 1099-INT, refund by paper check"). From your forms and message I already have:

- **Casey Rivera**, born 1996-07-14, shift lead, 88 W 5th Ave Apt 3, Columbus OH 43201 (matches the W-2 and 1099-INT), casey.rivera@checks.terminal.tax
- **Single**, no dependents, filed for 2024 with an AGI of $43,910, refund by paper check
- **W-2 from Riverbend Coffee Roasters:** $46,250 in wages and $4,180 of federal tax withheld, plus the Social Security, Medicare and Ohio boxes
- **1099-INT from Lakeside Credit Union:** $38.12 in interest, no withholding

No phone number is fine, since the template only asks for email.

Before sending, I need a few answers. The service only accepts facts you state outright and refuses a reply like "none of the other stuff" for these, so you can answer in a single line:

1. Is this your **original** 2025 return, not an amended one?
2. Were you a **U.S. citizen or resident alien** all of 2025, and did you live in the U.S. for more than half the year?
3. Do you have an **SSN valid for employment**? Just yes or no. Did the IRS issue you an **IP PIN** (Identity Protection PIN)? Yes or no, and don't share the PIN.
4. Is the 1099-INT the **final copy**, not a draft or one being corrected?
5. Were you **married** at any time in 2025, or in a **registered domestic partnership**?
6. To confirm, do all of these get a "no"? Blind, someone can claim you as a dependent, digital assets, self-employment or side-gig income.
7. **None of these apply**, right? Other income or tax forms, IRA/HSA activity, estimated or extension payments, credits, educator expenses, Marketplace coverage, carryovers, foreign accounts or trusts, interest that belongs to someone else, the kiddie tax, applying the refund to 2026.
8. **Choices:**
   - Standard deduction or itemize?
   - Claim the new tips, overtime, car-loan or senior deduction?
   - $3 to the Presidential Election Campaign Fund?
   - Let someone else discuss the return with the IRS?

A reply like "1 yes, 2 yes/yes, 3 yes/no, 4 yes, 5 no, 6 all no, 7 none, 8 standard/no/no/no" is enough. Then I'll send it and give you the link.

**Customer:** yeah it's my original 2025 return, i'm a us citizen and lived here all year, and my ssn is valid but i'm not putting it in a chat. no ip pin, the 1099 is the final copy, i'm single, and none of the other stuff applies to me. standard deduction, no to the campaign fund, and no to someone else talking to the irs.

**Assistant:**

Thanks, that covers nearly everything. I'll build the return from your answers and send it. Three items weren't answered explicitly:

- married at any time in 2025
- registered domestic partnership
- the tips/overtime/car-loan/senior deduction

I'll leave those blank so the service flags them, rather than guessing.

*Terminal Tax: Read the instructions for agents*

**Assistant:**

Only those three items are still open. Now I'll submit to see whether anything else gets flagged:

*Terminal Tax: Sent the prepared return for checking (returned items to fix)*

**Assistant:**

The service accepted all the other answers. It turned the packet down only because of the three blank items, and it didn't keep the packet. It needs a direct answer to each one. "Single" doesn't count as an answer to the first two:

1. Were you **married at any time during 2025**, even if not at the end of it?
2. Are you in a **registered domestic partnership** (California, Nevada or Washington)?
3. Do you want to claim the **deduction for qualified tips, overtime pay, or car-loan interest**? The senior part doesn't apply to you. Your W-2 shows no tips in boxes 7 or 8, but overtime or car-loan interest could still count.

A reply like "no, no, no" is fine. Then I'll resubmit and send you the link.

**Customer:** no, never married and not in a domestic partnership. no to the tips/overtime/car-loan deduction too, i don't have a car loan and no tips reported separately.

*Terminal Tax: Sent the prepared return for checking (accepted: filing link ready)*

**Assistant:**

The service accepted the return. Here's the link:

https://app.terminal.tax/file#09KiIE...

Before you open it, Terminal Tax asks that you check these answers from the return. Tell me if any are wrong, and I'll resubmit and get you a new link:

- This is your original 2025 federal return, not an amended one
- No estimated tax payments and no payment made with an extension
- No 2024 refund applied to 2025
- No K-12 educator expenses
- No mortgage credit certificate or mortgage interest credit carryforward
- No foreign financial accounts or foreign trusts
- No other tax credits claimed (education, child care, energy, retirement savings, clean vehicle)

The return is built from your two forms: $46,250 in W-2 wages with $4,180 of federal tax withheld, and $38.12 of credit union interest. You're filing single with the standard deduction and no dependents, and the refund comes as a paper check. Terminal Tax works out the actual refund, so check that figure on the review page.

On the page you'll enter the SSN, a one-time code sent to the casey.rivera@checks.terminal.tax address, and a signing PIN. Then you'll review the full Form 1040, sign and authorize payment.

**Before you sign,** make sure the page clearly shows it's a test or sandbox environment. Their public docs only describe live filing, and I couldn't confirm a test mode from my side. If anything there suggests it's live, stop before signing. Nothing is sent to the IRS until you sign.

**Customer:** perfect, thanks! opening it now

## The filing page

Casey opens her filing link. Her Social Security number, card and signature are typed only here, never in the chat. The page asks permission to use her tax data, confirms her email with a one-time code, confirms her details, takes her Social Security number, shows her tax forms as the chat described them, shows the complete return for review, takes a test card in the payment processor's fields, and takes a 5-digit signature PIN.

## Closing card

Signed and sent. The card is charged only if the IRS accepts the return, and the result arrives by email. Here everything was simulated on the test site.
