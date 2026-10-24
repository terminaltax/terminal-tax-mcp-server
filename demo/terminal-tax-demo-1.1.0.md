# Terminal Tax demo 1.1.0: transcript

[terminal-tax-demo-1.1.0.mp4](terminal-tax-demo-1.1.0.mp4) (3 min 42 s, no audio), recorded 2026-10-24 on the Terminal Tax test site (app.terminal.tax) with a fictional taxpayer, Casey Rivera. Nothing was sent to the IRS and no card was charged.

The chat is a real session, replayed: an AI agent (Claude Code, run headless, with the Terminal Tax connector) talking with a simulated customer who answers its questions in plain words and shares a W-2 and a 1099-INT as PDF files. The assistant's words are its own and are shown unedited, except that the filing link is shortened and one note is added after the hand-off message (below). The filing page part shows one fresh filing link made from the same prepared return.

## Title card

Filing taxes from a chat. A taxpayer talks with their own AI assistant, then reviews, signs and pays on one Terminal Tax page. Test site with a synthetic taxpayer: nothing is sent to the IRS and no card is charged.

## The chat

**Customer:** hey! can you help me get my 2025 taxes done? i'd like to file with terminal tax, i added it to my assistant

**Assistant:**

I'll start by loading the Terminal Tax tools and opening a filing session.

*Terminal Tax: Started a filing session*

*Terminal Tax: Read the return format*

**Assistant:**

I've opened a Terminal Tax filing session for your 2025 federal return. One thing first: today is October 24, 2026, so both the April 15 deadline and the October 15 extension deadline have passed. If you're getting a refund, there's no penalty for filing late. If you owe, penalties and interest are building up, so it's worth filing soon.

Some limits on what Terminal Tax covers:
- It only does the **federal return** (Form 1040). It doesn't file state or local returns, so you'd do your state return separately.
- **You never give me your SSN.** You type it yourself on the Terminal Tax filing page, where you also review and sign the return. Nothing goes to the IRS until you sign there.

To get started, please send me your tax documents. You can paste them, or give me file paths if they're PDFs or images on this machine. Common ones:
- **W-2s** from your jobs
- **1099s**: 1099-INT (bank interest), 1099-DIV (dividends), 1099-B (stock sales), 1099-NEC or 1099-MISC (freelance or contract work), 1099-R (retirement payouts), 1099-G (unemployment or a state refund)
- **SSA-1099** if you get Social Security
- **1098** (mortgage interest) or **1098-E** (student loan interest)

Also tell me a bit about your situation:
1. Your filing status: single, married filing jointly, married filing separately, or head of household
2. Whether you have any dependents
3. Whether you had any self-employment, rental, or crypto income

Once I see your forms, I'll pick the closest starting template and send you every remaining question at once, so you can answer them in one reply.

**Customer:** single, no dependents, and none of the self-employment, rental, or crypto stuff applies to me. here's my W-2 *(attached: casey-w2-2025.pdf)*

*Terminal Tax: Read the return format*

**Assistant:**

I've read your W-2, and it matches Terminal Tax's simplest case: single, one W-2, standard deduction, with a refund. Using the 2025 standard deduction of $15,750, I estimate a refund of about **$750**. Terminal Tax works out the exact figure.

**From your W-2 (Riverbend Coffee Roasters LLC, EIN 12-3456789):** wages $46,250.00 and federal tax withheld $4,180.00. Your Ohio state tax ($1,120) and local tax ($925) are also on it, but those only matter for your state and city returns, which Terminal Tax doesn't file.

I've noted that you're single, have no dependents, and had no self-employment, rental or crypto income. Please answer the numbered questions below in one reply. Short answers are fine, like "1. yes 2. 1990-05-12, barista…".

**A. Your details** (you'll type your SSN on the filing page, never here)
1. Your W-2 shows **Casey Rivera at 88 W 5th Ave Apt 3, Columbus, OH 43201**. Is that your legal name exactly as it appears on your Social Security card, and your current mailing address? If anything is different, tell me the correct version.
2. Your date of birth and your occupation.
3. Your email address and mobile number. The filing page sends a one-time code and the IRS result there.
4. Did the IRS give you an Identity Protection PIN (IP PIN) for this filing season? Just yes or no. Never tell me the PIN itself.
5. Did you file a federal return for 2024? Have you ever filed one, for any year? If you filed for 2024, what was the AGI on line 11 of that return? It's fine if you don't know.

**B. About you**
1. Were you married at any point during 2025, even if not at the end of the year? Are you in a registered domestic partnership in California, Nevada or Washington?
2. Were you a U.S. citizen or U.S. resident alien (for example, a green card holder) for all of 2025?
3. Did you live in the U.S. for more than half of 2025?
4. Were you born before January 2, 1961? If so, do you want Form 1040-SR, the larger-print version? The tax is the same.
5. Were you blind at the end of 2025?
6. Can anyone, a parent for example, claim you as a dependent on their 2025 return?
7. Do you have a Social Security number that's valid for work, rather than an ITIN? Just yes or no.

**C. Your 2025.** Besides the W-2, did any of these apply to you? Reply "none" or name the ones that do:
- Any other tax form: 1099-INT, 1099-DIV, 1099-B, 1099-NEC, 1099-MISC, 1099-R, 1099-G, SSA-1099, 1098, 1098-E or 1098-T
- A Schedule K-1 from a partnership or S corporation
- A traditional IRA contribution to deduct, or any money into, out of or rolled over between IRA, HSA, Archer MSA, Coverdell or ABLE accounts
- Exercising incentive stock options (ISOs)
- Estimated or extension tax payments for 2025, or a 2024 refund you applied to 2025
- Wanting part of your refund applied to your 2026 estimated tax
- A tax credit to claim (earned income, education, child care, energy, saver's or clean vehicle), or a mortgage credit certificate
- K-12 classroom expenses as a teacher
- Health coverage through the Marketplace (Form 1095-A)
- A capital loss or business loss carried over from 2024
- A foreign bank or financial account you owned or could sign on, or any involvement with a foreign trust
- Being under 24 and someone's dependent child or student with investment income
- This being an amended 2025 return rather than your first one

**D. Your choices**
1. Standard deduction, or itemize? Standard is almost certainly better for you.
2. Do you want to claim the new deductions for qualified tips, qualified overtime pay, or car loan interest?
3. Do you want $3 to go to the Presidential Election Campaign Fund? This doesn't change your tax or refund.
4. Do you want to let someone else discuss this return with the IRS?
5. Do you want your refund by direct deposit (recommended) or paper check? For direct deposit, give me the routing number, the account number, and whether it's checking or savings. I'll read the account back to you once to confirm.

Once I have your answers, I'll check the return with Terminal Tax and send you the link to review and sign it.

**Customer:** yep, casey rivera at that address is right, born july 14 1996, i'm a shift lead at a coffee roastery, email casey.rivera.demo@terminal.tax, mobile (702) 958-0123. no ip pin, i filed 2024 myself and the agi was 43910, i'm single, nobody can claim me, and i was a us citizen and lived in the us all year, here's the credit union form too. none of the other stuff applies to me, standard deduction is fine, and a paper check for the refund is good. *(attached: lakeside-1099-int-2025.pdf)*

*Terminal Tax: Read the return format*

**Assistant:**

Thanks, I've got almost everything. I read the Lakeside Credit Union 1099-INT: **$38.12** in interest (box 1), no federal tax withheld, payer TIN 31-0987654. That interest is taxable, but it only lowers your refund by about $5, so it should still be around **$750**.

There are a few questions your reply didn't cover, plus two new ones that come with the 1099-INT. Please answer each:

1. Were you **married at any point during 2025**, even if you were single by December 31? Are you in a **registered domestic partnership** in California, Nevada or Washington?
2. Were you **blind** at the end of 2025?
3. Is your Social Security number **valid for work**, rather than an ITIN? Just yes or no.
4. Is the 1099-INT the **final copy**, not a draft or one the credit union said it would correct?
5. Did any of that interest **belong to someone else** (a nominee), or include accrued interest, bond adjustments, or U.S. savings bond interest?
6. Do you want to claim the new deduction for **qualified tips or qualified overtime pay**, or for **car loan interest**? As a shift lead, check whether you were paid overtime in 2025. Your W-2 shows no reported tips.
7. Do you want **$3 to go to the Presidential Election Campaign Fund**? It doesn't change your tax or refund.
8. Do you want to let **someone else discuss this return with the IRS**?

Once you answer these, I'll submit the return to Terminal Tax and send you the link to review and sign it.

**Customer:** nope on the married and domestic partnership stuff, i've always been single. not blind. my ssn is valid for work. the 1099-INT is the final copy, nothing's been corrected, and none of that interest was someone else's. no tips, no car loan, and i'll check with the cafe about overtime. no to the $3 and no to someone else talking to the IRS.

**Assistant:**

Thanks, that covers everything except the overtime question. I'll check the rest of the return with Terminal Tax now, so the overtime answer should be the only thing left. First I need the definitions of a few remaining fields.

*Terminal Tax: Read the return format*

*Terminal Tax: Sent the prepared return for checking*

**Assistant:**

Your return is ready except for one answer: whether you'll claim the **overtime deduction**. Terminal Tax checked everything else and found no other problems. Since you said no to tips and the car loan, that's the only open item.

**What to ask the cafe**
- The deduction only covers the **extra "half" of time-and-a-half**, not all the pay for those hours. For example, if your normal rate is $18/hour and overtime pays $27, only the extra $9 per overtime hour counts. Ask for that total for 2025.
- Your W-2 has nothing in box 14. That's allowed for 2025, because employers didn't have to report overtime on the W-2 this year. Many are giving employees a separate statement or a payroll summary instead.
- It's worth asking about. You're in the 12% bracket, so every $1,000 of overtime premium adds about $120 to your refund, on top of the roughly $750 estimate.

**Then reply with one of these:**
- **"No overtime"** (or "I don't want to claim it"): I'll submit right away and send you the filing link.
- **"Yes, the overtime premium was $X"**: I'll add the deduction and send you the link. If the cafe gives you a statement, attach it and I'll read the amount from it.

When you open the link, you'll type your SSN, review the full return, and sign it. Nothing goes to the IRS until you do. Your refund will come as a paper check to 88 W 5th Ave Apt 3. Ohio and Columbus returns aren't included, so file those separately.

**Customer:** no overtime, i didn't get any extra overtime pay beyond what's on the w-2. go ahead and submit it.

*Terminal Tax: Sent the prepared return for checking*

**Assistant:**

Terminal Tax accepted your return. It's saved as an unsigned draft, and **it hasn't been filed yet**. You finish it here:

**https://app.terminal.tax/file#0ct7WC...**

**On that page you'll:**
1. Give permission and confirm your details: Casey Rivera, 88 W 5th Ave Apt 3, Columbus OH 43201, born 7/14/1996.
2. Type your **Social Security number**. If the page asks for your 2024 AGI to verify your identity, it's **$43,910**.
3. Review the full Form 1040 and the exact refund amount. My estimate is about **$745**.
4. Sign with the one-time code sent to casey.rivera.demo@terminal.tax or (702) 958-0123. That's when the return is sent to the IRS, and the IRS result comes to the same email and phone.

**What's on the return:**
- **Income:** $46,250 in wages from Riverbend Coffee Roasters and $38.12 in interest from Lakeside Credit Union.
- **Deduction:** the standard deduction.
- **Credits and extra deductions:** none. You don't qualify for the earned income credit at your income level without children, and you aren't claiming any of the new deductions (tips, overtime, car loan, senior).
- **Refund:** a paper check to your Columbus address, no $3 to the Presidential Election Campaign Fund, and no one else authorized to talk to the IRS for you.

The link can expire, and nothing is filed or charged if it does or if you don't finish. If that happens, tell me and I'll get you a new one. Your Ohio and Columbus returns aren't part of this, so you still need to file those separately.

*Note added for this video: on the filing page the emailed code only confirms Casey's email address; she signs with a 5-digit PIN she chooses, and the IRS result arrives by email.*

**Customer:** perfect, thanks! opening it now

## The filing page

Casey opens the one link the assistant returned. Her Social Security number, card and signature are typed only here, never in the chat. The page asks permission to use her tax data, confirms her email with a one-time code, confirms her details, takes her Social Security number, shows her tax forms as the chat described them, shows the complete return for review, takes a test card in the payment processor's fields, and takes a 5-digit signature PIN.

## Closing card

Signed and sent. The card is charged only if the IRS accepts the return, and the result arrives by email. Here everything was simulated on the test site.
