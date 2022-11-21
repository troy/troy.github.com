---
layout: post
title: Examining borrower privacy in peer-to-peer lending
date: Aug 21, 2012
redirects:
- /borrower-privacy-in-peer-to-peer-lending
---

I just [noticed](https://twitter.com/troyd/status/238085893280395264) that the sales reports published by [Lending Club](http://lendingclub.com/) contain enough personally-identifiable information (PII) to be, well, personally-identifiable. Per the instructions on their [privacy policy](http://www.lendingclub.com/public/privacy-policy.action), I emailed this to the privacy role account.

As a point of reference, here's the equivalent [prospectuses](http://www.prosper.com/prospectus/) and an example [sales report](http://www.prosper.com/published/sec/sales/2012/sales_20120820-0900.htm) from Prosper. Prosper doesn't seem to publicly disclose a borrower's employer or city, only an job category and a state. Prosper's freeform loan descriptions are more detailed and the borrower sometimes refers to a location, but the aggregate information is still not generally enough to identify the borrower, and never is unless the borrower over-discloses. I am not affiliated with either service.

Here's the email to Lending Club (August 21, 2012) and their reply (September 6, 2012):

* * *

Hi all,

I'm a prospective lender and I just skimmed the [prospectuses](https://www.lendingclub.com/info/prospectus.action) and the [sales report](https://www.lendingclub.com/info/sales-reports.action) filings, then I read them, the [privacy policy](http://www.lendingclub.com/public/privacy-policy.action), and the [privacy section](http://www.lendingclub.com/kb/index.php?CategoryID=19) of Lending Club's knowledge base in more detail. The privacy policy contains two material discrepancies, one of which I believe is substantial. I explain the discrepancies in detail below.

I believe the fix is relatively simple: the new borrower signup process, the privacy policy, and the knowledge base privacy section should all contain visible, obvious links to the sales reports. Right now they're buried, and the privacy policy spends lots of words to (incompletely) describe how much will be disclosed. The borrower should be shown the actual information which will be disclosed about them, using the existing sales reports as an example. I believe this description explains the disclosure much more clearly:

> If your loan is funded, Lending Club must publicly disclose certain information about you as part of public SEC filings. This includes employer, year hired, city, income, loan reason, and credit information. [Click here to see examples of Lending Club loan disclosures](https://www.lendingclub.com/info/sales-reports.action).

I'm spending the time to write all of this down because I want to see peer-to-peer lending and Lending Club succeed, so please let me know if I can clarify anything here. Here's more details about the 2 discrepancies:

1. The information disclosed about borrowers in sales reports is enough to identify many of them individually. Although the information doesn't contain a real name, the privacy policy states:

    > Personal but not personally identifiable information about borrowers is contained in loan listings that can be viewed by all users and is filed with the Securities and Exchange Commission and as such is made publicly available.

    This is inaccurate. Using the information on Lending Club's sales reports, I could personally identify many individual borrowers, and take an educated guess about many more. In some cases this would take a bit of existing information, such as from discovering a loan request from a co-worker based on their listed employer. I can almost guarantee that another employee of Friendship Public Charter School, Reis Law, pair Networks, Fundly, and many other small- and mid-size employers listed on the 2012-08-21 sales report could name the borrower using only information from the report.

    In other cases, the combination of employer, year hired, city, income, and freeform text description is enough for a stranger to identify them using relatively simple Google, LinkedIn, or Facebook searches. For many companies, the combination of those fields is unique throughout the whole company. It's often very unique, like because only a few people were hired in a given year. Also, the "Earliest credit line" field is often a reasonable proxy for the borrower's age, and is at least a minimum age.

    In those cases, a single external corroboration such as a LinkedIn job announcement, a title transfer on BlockShopper, or a Facebook photo posted to the company's page could be enough to attach a name.

2. The credit score information is both public and disclosed alongside other information which is personally identifiable. The data disclosure section says:

    > Qualified Lending Club investors will also see certain credit data collected from or calculated based on your credit bureau file. It is necessary to allow prospective investors to see this information as they evaluate your loan request. The information displayed to investors includes a credit profile section and a credit history section. As noted above, this information is also contained anonymously in loan data files available on the statistics page.

    It goes on to define the fields disclosed as part of the credit profile and the credit history.

    It doesn't say that the credit information is disclosed alongside lots of other personal data. Even when that information is not enough to be personally-identifiable (discrepancy #1 above), it's public and visible to anyone. It's not visible only to "Qualified Lending Club investors," and perhaps more importantly, the disclosure is not on a loan-by-loan basis. In reading the paragraph above, I would interpret it to say that my information will be temporarily disclosed to all qualified lenders (prospective investors) while my loan is being funded, then will be only shown to those lenders who actually funded my loan. That isn't the case.

Thanks,

Troy

* * * 

Reply from Mark D'Arrigo, Associate Counsel, Lending Club:

> Mr. Davis:
> 
> Thank you for your email regarding the protection of personally identifiable information on the Lending Club website.  Lending Club takes consumer privacy seriously and has implemented procedures and policies designed to protect consumer information.  We appreciate your detailed feedback and have discussed your suggestions regarding our Privacy Policy and disclosures to members.  However, we believe that our Privacy Policy is consistent and does not contain material discrepancies.
> 
> As part of our consumer privacy efforts, Lending Club informs applicants regarding the type of information that will be disclosed to the public both in the Privacy Policy itself and throughout the application via the use of tool tips, a pop-up that notifies the applicant that information placed into certain fields is made available to the public.  We also review loan titles and free-form answers provided by applicants in an attempt to limit the exposure of personally identifiable information that applicants may provide outside the marked application fields.  Lastly, credit information is only available for viewing by Lending Club members and not available to non-members merely perusing the site.  As you noted, from the information available on our site, members such as yourself can view the information about borrowers that Lending Club must file with the Securities and Exchange Commission.  We do not agree, however, that this constitutes "personally identifiable" information.  Your letter indicates that you were only able to take an "educated guess" about the identity of some borrowers using information you gathered from other sources.  The fact that certain limited information regarding borrowers is viewable through the Lending Club website -- which, again, Lending Club flags as publicly disclosed in the application itself and in our Privacy Policy -- and that similar information may also be available through external sources that contain additional information does not, in our view, indicate that Lending Club displays personally identifiable information or that our Privacy Policy contains material discrepancies.  We also do not believe that the manner in which certain personal information is presented on the website is inconsistent with our Privacy Policy or other consumer protection initiatives.
> 
> Although we disagree with your conclusions and interpretations, we appreciate your email and thank you for your feedback.  We periodically review our consumer privacy policies and processes and will take your specific suggestions under consideration as part of that review process.  Thank you very much for your time and your interest in Lending Club.
> 
> Sincerely yours,
>
> Mark D'Arrigo
>
> Associate Counsel