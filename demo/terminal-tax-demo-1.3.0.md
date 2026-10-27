# Terminal Tax demo 1.3.0: transcript

[terminal-tax-demo-1.3.0.mp4](terminal-tax-demo-1.3.0.mp4) (2 min 3 s, no audio), recorded 2026-10-26 on Terminal Tax's test site (app.terminal.tax) with a fictional taxpayer, Casey Rivera. Nothing was sent to the IRS and no card was charged.

The chat is a real session in Claude Code on the web (claude.ai/code), shown in its own browser window, with nothing installed or connected. Casey's side was typed by a simulated customer working from Casey's facts; Casey attaches a W-2 and a 1099-INT as PDF files and first asks only for help working out the taxes. When Casey asks it to file with Terminal Tax and names the test site, the assistant reaches Terminal Tax by itself with ordinary web requests and hands over a private filing link. The filing page part is the same browser opening that link: the emailed one-time code, the complete return to review, Stripe's test card, the signature, and then the IRS answer by email from the test site's simulated IRS. Stretches where the assistant is only working are sped up and marked on screen; the sidebar's session list and account row are blurred. The assistant's words are its own, unedited except that the filing link is shortened. What the assistant says Terminal Tax covers describes the service on the recording date; the current scope is at https://terminal.tax/llms.txt.

## The chat

**Casey:** hey, can you help me figure out my 2025 taxes? my W-2 and a 1099-INT from my credit union are attached
*(attached: casey-w2-2025.pdf, lakeside-1099-int-2025.pdf)*

**Assistant:**

The file reads didn’t return the PDF text, so I’ll extract it directly.

Extracted text from both tax PDFs



Extracted text from both tax PDFs

I’ve got both forms, and the 2025 federal return looks like a refund of about $755. That assumes you file as single with no dependents and had no other income, so please check those.

What’s on your forms

W-2 (Riverbend Coffee Roasters): wages of $46,250.00 and federal tax withheld of $4,180.00. Ohio withholding is $1,120.00 and local withholding is $925.00.

1099-INT (Lakeside Credit Union): interest income of $38.12, with no tax withheld.

Federal estimate (single filer)

Wages	$46,250.00

Interest	$38.12

Adjusted gross income	$46,288.12

Standard deduction (2025, single)	−$15,750.00

Taxable income	$30,538.12

Tax (10% up to $11,925, 12% above that)	about $3,425

Federal tax withheld	$4,180

Estimated refund	about $755

Two things to know:

Timing: the normal April 15, 2026 deadline has already passed. If you’re owed a refund, there’s generally no penalty for filing late. You usually have three years from the original due date to claim it, so the 2025 refund is still available through April 2029. If you owe, penalties and interest may apply.

Ohio and local: I haven’t calculated these. The $1,120 of Ohio withholding and the $925 of local (probably Columbus) withholding will probably produce a small refund or balance on those returns. I can estimate them if you want.

Please tell me:

Is your filing status single, or something else?

Do you have dependents, or any other income, such as a side gig, 1099s, or unemployment?

Do you have deductible expenses, such as student loan interest, an IRA contribution, or HSA contributions? These would lower the tax.

Free e-file is available through IRS Free File or Direct File (if still offered) if you’d rather not pay for software.







**Casey:** single. no dependents or other income. no deductible expenses.

**Assistant:**

Your answers match what I assumed, so the estimate stands: a federal refund of about $755.

Adjusted gross income	$46,288.12

Standard deduction (single)	−$15,750.00

Taxable income	$30,538.12

Tax	about $3,425

Federal withholding	$4,180

Refund	about $755

The exact figure may differ by a dollar or two. The IRS tax table works in $50 income steps, and tax software will use that.

How to file

Use the IRS Free File options or your preferred tax software. Your return is simple, so the free tiers should cover it. Enter the W-2 and 1099-INT exactly as printed.

Pick the standard deduction. With no deductible expenses, it beats itemizing.

Choose direct deposit for the fastest refund.

File the Ohio return too. You had $1,120 withheld, so you’ll likely get some of it back.

Check your Columbus city return. You had $925 withheld for local tax. Ohio cities usually require their own return or reconciliation.

You’re past the April 15, 2026 deadline, but with a refund due there’s generally no late-filing penalty. You have until April 2029 to claim it. File soon, since the longer you wait, the longer you go without the money.

I can estimate the Ohio and Columbus returns if you want. I’d need to know whether Columbus is your city of residence and work.







**Casey:** nice, thanks! can you just file it with the IRS for me? use Terminal Tax. i'm on their test site, app.terminal.tax (their guide is at app.terminal.tax/llms.txt)

**Assistant:**

I’ll start by reading their guide.

Fetched a page, used a tool

Terminal Tax can file this, but I need some details from you first. Their guide covers federal returns only, so Ohio and Columbus would still be separate.

What I need from you

Full legal name, date of birth, and mailing address. The W-2 shows 88 W 5th Ave Apt 3, Columbus OH 43201. Is that current?

Occupation.

Email and mobile number.

Bank routing and account numbers for the refund direct deposit.

Your 2024 filing status and 2024 AGI. If you didn’t file for 2024, tell me.

Three yes/no answers: are you blind, are you 65 or older, and can anyone claim you as a dependent? They won’t accept a blank for these.

What I won’t handle

Your SSN, any IRS Identity Protection PIN, the signing PIN, and email one-time codes. You enter those yourself on their filing page, and their service rejects packets that contain them.

Card details. The $19.99 fee is charged only if the IRS accepts the return, and you enter the card in Stripe’s fields.

One thing to know about the order of steps. Their process has me submit your packet, including your bank account details, before you review and sign on their page. They say the data is held sealed and erased if you decline or the link expires. That’s their claim and I can’t verify it. If you’re not comfortable with that, you can enter everything on their site yourself and skip the pre-submission step.

If you want to go ahead, send the details above. I’ll build the return from your W-2 and 1099-INT and give you a link to review and sign.







**Casey:** My legal name is Casey Rivera, my date of birth is July 14, 1996, and my mailing address is 88 W 5th Ave Apt 3, Columbus OH 43201. I’m a coffee roastery shift lead. I’m not sure about my email yet, and I’d rather not give a mobile number or bank details. I filed as single in 2024, and my AGI was $43,910. I’m not blind, I’m under 65, and nobody can claim me as a dependent. I’ll enter my SSN myself on the e-file signing screen. I’d like to go ahead and get the filing link.

**Assistant:**

I’ll open a filing session and look at the packet schema. I’ll leave the email, phone, and bank fields blank rather than make anything up.

Ran 4 commands

A paper-check refund template exists, so you wouldn’t need to give bank details. Let me get it.

Ran 2 commands (1 failed)

The persisted file is plain text rather than JSON, so I’ll read the saved response from my own copy.

Printed template questions and presets



Printed template questions and presets

I’ve opened a filing session with Terminal Tax. Nothing has been sent about you yet. The packet has to come from your own answers, so I can’t fill in blanks for you, and I need a few more things before I can get you a link.

Your situation

Email: it’s required. The one-time code and the IRS result are sent there. Any address you can open today works, including a new free one.

Mobile number: optional, so you can skip it.

Refund: the paper-check version of the return doesn’t need bank details. Do you want a paper check? It will arrive more slowly than direct deposit.

Please answer each numbered item:

Did the IRS issue you an Identity Protection PIN for this filing season? Yes or no only, never the PIN.

Did you file a federal return for 2024, and have you ever filed one? Your 2024 AGI of $43,910 is noted.

Is your 1099-INT the final copy, not a draft or one the credit union said it will correct?

Were you married at any time in 2025? Are you in a registered domestic partnership?

Were you a U.S. citizen or resident alien for all of 2025, and did you live in the U.S. for more than half the year?

Do you have a Social Security number valid for employment? Yes or no only.

Do you want the standard deduction?

Do you want a deduction for qualified tips, qualified overtime pay, or car loan interest?

Do you want $3 to go to the Presidential Election Campaign Fund?

Do you want to let another person discuss this return with the IRS?

Other 2025 situations. Did any of these apply to you? Reply “none” or name each one that does.

Crypto or other digital assets.

Side-gig, freelance, or cash income, even without a tax form.

Any other tax forms or income.

Rental income or a K-1.

IRA, HSA, or similar account activity.

Estimated or extension tax payments, or a 2024 refund applied to 2025.

A tax credit you want to claim.

Educator expenses.

Marketplace health coverage.

A loss carried over from 2024.

Foreign accounts.

Interest that belonged to someone else, or savings bond interest.

This being an amended return.

I also need to know whether your W-2 and 1099-INT are standard printed forms (not handwritten or altered), and whether the name and address on both are yours. They show Casey Rivera at 88 W 5th Ave Apt 3, Columbus OH 43201, which matches what you gave me.

**Casey:** I do have the required email, and I want a paper check. I don’t have an IRS Identity Protection PIN. I filed my 2024 federal return myself. My 1099-INT is the final copy. I was never married and I’m not in a registered domestic partnership. I was a U.S. citizen and lived in the U.S. all of 2025. My Social Security number is valid for work; I’ll type it myself on the e-file signing screen. I want the standard deduction. I don’t want deductions for tips, overtime, or car loan interest. No to the $3 campaign fund, and no third-party designee.

My only income was $46,250 in W-2 wages and $38.12 in interest. No crypto or digital assets, side gigs, other income or tax forms, rental income, or K-1. No IRA, HSA, or similar account activity. No estimated or extension payments, no 2024 refund applied to 2025, and no credits or educator expenses. No Marketplace coverage, carryover loss, foreign accounts, interest belonging to someone else, or savings bond interest. This is not an amended return. Both forms are standard printed copies with my correct name and address.

**Assistant:**

Thanks, that covers almost everything. I need two more things before I can submit:

Your email address. You said you have one, but you didn’t give it to me. It goes in the return so the one-time code and the IRS result reach you.

Refund applied to 2026: do you want any part of your refund applied to your 2026 estimated tax? Yes or no. I’m asking because your list didn’t mention this one.

Once I have those, I’ll build the packet, submit it, and give you the filing link. It’s good for 15 minutes after it’s issued, so have your SSN and a card ready. The $19.99 fee is charged only if the IRS accepts the return.

**Casey:** My email is pccaseyriveramvq1bi57da05@checks.terminal.tax. No, don’t apply any refund to 2026. I’ll enter my SSN myself on the e-file signing screen.

**Assistant:**

Now I’ll build the packet from the template.

Ran 2 commands

The return is submitted and the link is ready. Nothing has been filed or charged yet.

Before you open it, please check these answers from your packet and tell me if any are wrong:

This is your original 2025 federal return, not an amended one.

You made no estimated tax payments for 2025.

You made no payment with an extension.

You applied no prior-year refund to 2025.

You claimed no K-12 educator classroom expenses.

You have no mortgage credit certificate and no mortgage interest credit carryforward.

You have no interest in or signature authority over a foreign financial account, and no foreign trust.

You’re claiming no other tax credits (education, child care, energy, retirement savings, clean vehicle, or other).

If anything is wrong, tell me and I’ll send a corrected packet. That gives you a new link, and this one stops working.

https://app.terminal.tax/file#… (single-use link, shortened here)

If the link doesn’t open when clicked, copy all of it into your browser’s address bar.

What you do on that page

Read the privacy notice and give permission. If you decline or the link expires, they erase the data.

Enter your SSN and complete the identity steps. The one-time code goes to the email you gave.

Review the full return and confirm the refund figure matches my estimate of about $755.

Enter your card in Stripe’s fields. The $19.99 fee is charged only if the IRS accepts the return.

Sign.

The link works for 15 minutes after it’s first issued. If it lapses, I can submit the same packet again for a fresh one. Terminal Tax will email you the IRS accepted or rejected result, and I can’t check it for you.

Two facts I filled in from what you told me, so check them on the review screen:

Credits: I treated your “no credits” as also covering the mortgage credit certificate and the earned income credit.

SSN: I recorded that your SSN was issued before the filing deadline.

This is the federal return only. Your Ohio state return and Columbus city return are still separate, and I can help estimate them.

## The filing page

Casey opens the link in the same browser. She allows Terminal Tax to use her tax information to file, types the 6-digit code emailed to her, types her Social Security number (on the page only, never in the chat), reviews the complete return (refund $755, mailed as a check), adds Stripe's test card (charged only if the IRS accepts the return), and signs with a 5-digit PIN. The page answers: "Signed. Your return is on its way to the IRS."

Two minutes later an email says the IRS accepted the return. On the test site that answer comes from a simulated IRS and no card is charged.
