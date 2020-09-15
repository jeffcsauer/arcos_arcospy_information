Hi @edonnachie,

Thank you so much for the detailed comments! They were very helpful for improving the paper. I have updated the `paper.md` with several changes and provide responses to each of your comments below. 

---

*Author responses to reviewer comments:*

> Comment #1: It would be helpful to explain what the Opioid Overdose Crisis is, perhaps with link to the CDC. It's not clear to me whether the overdoses are accidental (due to overuse of this drug therapy) or suicide-related (due to the controls being too lax).

This is an excellent point. I have done a few things to address your comment. Firstly, I rewrote the opening of the introduction to contextualize the U.S. Opioid Overdose Epidemic. Secondly, I added the phrase "all-cause" when describing the increases in opioid-involved mortality as the Opioid Overdose Epidemic is concerned with both unintentional, intentional, and homicidal drug-involved deaths. The system-level *cause* (e.g. 'overuse of this drug therapy' or 'controls being too lax') remains an active area of research.  

> Comment #2: You write that data was released until 2012. You should mention here that the data for 2013-2014 is now also available.

Clarified that additional data for 2013-2014 is now also available. 

> Comment #3: You write that patient confidentiality is one reason that access to ARCOS is usually restricted. If this were true, then providing wide access to this data would be legally and ethically problematic (at least from a European perspective). However, I would tend to the view that the risk of revealing information about patients is negligible. Either way, this needs some explaining.

After consultation with co-authors I have reworked this sentence. Firstly, I replaced the word 'restricted' with 'only for approved requests (e.g. research or litigation)'. I have also added a citation for the Drug Enforcement Administration (DEA) Privacy Impact Assessment, which offers extremely detailed information on potential privacy concerns for the ARCOS data. I have also added the word 'anonymized' in the following sentence to clarify that no patient-level identifying information (e.g. name) exists in the present ARCOS data. The present ARCOS data represents *shipments* of controlled opioid medications from manufacturers to distributors, so you are correct in that  revealing information about patients is negligible. The original wording of the sentence was unclear and we hope that the new phrasing is helpful.

> Comment #4: Both from a technical and a data protection perspective, it would seem important to explain what is behind the API: How and where are the data stored? Who controls and maintains this database? Are requests logged, and if so, are personally identifiable data kept (e.g. IP address)?

I have added additional information on the API in the **API Structure** section including API specification and guidelines on use. I have reached out to members of the Data Reporting Team at *The Washington Post* for exact details on your comments regarding if and what personal identifiable information is stored.

> Comment #5: You should explain why the ARCOS database is useful. How does this compare with other sources of prescribing data (pharmacy data centres, medicaid etc)? I suspect that the main advantage lies in the analysis of how market dynamics facilitated the epidemic.

This is a great point. We feel that the first part of the comment ("How does this compare with other sources of prescribing data (pharmacy data centres, medicaid etc)?") is addressed by the sentences in the **Statement of Need** section. However, we have added additional sentences relating to the second point of the comment ("I suspect that the main advantage lies in the analysis of how market dynamics facilitated the epidemic.") as this is indeed a very important aspect of the Opioid Overdose Epidemic that has ample room left for exploration and quantification. 

> Comment #6: Repeated word: "In raw format, the the ARCOS database "

Deleted repeated word.

> Comment #7: Should "from 2006 to 2012" not be "from 2006 to 2014"?

Changed 2012 to 2014.

> Comment #8: The statement "while still maintaining individual medical privacy " is confusing, see above.

This is a great point. I have removed the quoted phrase as it is confusing and unnecessary.

> Comment #9: What you don't mention is that the data provide a different perspective to the medical claims data that would usually be used for such analyses. If I understand correctly, you're not looking at who received an opioid, but at how these substances traveled across the supply chain (and in what quantity). I think this is an important and interesting distinction to be made.

See author response to Comment #5 above. We agree and have added additional sentences relating to potential analyses of opioid prescription market dynamics.