# Paper Revision Changelog

Thank you for the excellent feedback on the first submission of the "fertile" manuscript. Below are our responses to the comments made by the Associate Editor and Reviewer:


**Associate Editor’s Comments:**

*p. 1: I suggest removing the parentheses from the abstract and replacing with commas.*

Great suggestion. This has been changed. A similar piece of text later in the manuscript had the same parentheses and these have been removed as well.

*p. 1: Collapse the parenthetical citations starting with Eisner 2018 into a single \citep (not \cite) command, with citations separated by commas within the \citep command, and don't add an extra set of parentheses.  Make this change throughout the manuscript, noting the difference between \citep and \cite.*

The citations throughout the manuscript have now been changed. Parentheticals are now in \citep format, while in-text citations are \citet.

*p. 2: You might want to cite R itself.*

A citation for R has been added just before the literature review section.

*p. 2:  "language and conceptual framework ... varies" -> "language and conceptual framework ... vary"*

This grammatical mistake has been corrected.

*p. 6: In Section 3.4, it might help some readers if you provide a short explanation of what a shim is.*

Good point. To address this, I added a new sentence explaining the definition of a shim in computer science before proceeding to describe their purpose in fertile.

*p. 8: In Section 3.5.4, Do you want to address whether fertile has any way of checking that particular versions of any dependencies are in place? I presume that package versions that change over time can sometimes destroy reproducibility.*

This feature (version-specific dependency tracking) has been added to fertile since the original manuscript was submitted. A short section detailing the new functionality is now at the bottom of the existing section on project dependency management right after the code for proj_pkg_script().

*p. 10:  Too bad the pandemic interrupted your cool-sounding study!  It does seem that the study could be run in an online-only class environment though; is this true and is it worth mentioning?*

Yes, this is true! Since the submission of the original manuscript, we decided to conduct another trial in the classroom in fall 2020, now that Smith College is 100% online. The text has been updated to reflect this.


**Reviewer’s Comments:**


General:
*- the use of shims is likely unfamiliar to R users. Therefore, I have some concern about the ability of a user to control how aggressively this package performs. For example, if a user specifies an absolute path and receives an error message, it will be difficult for the user to determine what function was used to specify this error message and determine if there is a way to be less aggressive (to turn that into a warning, instead of an error, for example). My fear is that this functionality may limit use. However, I do like that the sandbox() function addresses this to an extent, allowing users to test things out and "get it right" before retuning to where the original error message was received.* 

This is an excellent point! Part of the reason that fertile is so strict on this behavior is that in my own personal experience, many R coders (particularly those with little experience) tend to ignore warnings as long as their code executes properly. Having fertile’s path-related behavior be error based ensures that no one will skip over the messages that come up. However, my co-author and I do recognize that some users may still want to run these functions despite the warnings. In order to take this into account, we have added detail to the error messages produced by the shims. The new messages provide users with a method to override the error produced by fertile.

Specific minor suggestions (in order of manuscript):

- *A few suggested references to include in Intro and/or 2.1:* 
    - *reproducibility framework: Patil et al. (https://www.nature.com/articles/s41562-019-0629-z)*
    - *good enough practices: Wilson et al. (https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005510)*
    - *best practices: Wilson et al (https://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1001745)*

The first reference was an excellent fit for the introduction, and has been added there, while the second and third fit well into the literature review and have been mentioned accordingly.  

- *Section 2.3: currently there are too many vague phrases "some information," "a wide variety of aspects," "offering benefits," "provides benefits," etc. - description here limits readers ability to truly understand what your work does to build on the shortcomings in 2.2. For a more specific example, Docker/CI is described in 2.2 and it's not until the end of the paper (3.5.4) that I have a good sense as to whether this work addresses those shortcomings. Would love more specifics in 2.2.*

Many of the vague phrases in 2.3 now have more specifics attached to them. This should help clarify the benefit of fertile compared with some of the shortcomings in 2.2.

- *Section 3.1: may be helpful to be very clear here that these are errors and not warnings. "catches" wasn't clear as to whether I would be allowed to specify an absolute path and would get a warning, or whether this would aggressively error. (Note: the code makes this clear, but the text may benefit from slight clarification).*

This has been clarified in the text. In addition, further explanation of the difference in response between the read.csv() and setwd() examples has been provided.

- *3.2 `list_checks()` is a nice function, but a table with the checks and a brief description of what that check does in the paper would be beneficial.*

This table has been added! Since list_checks() provides no additional benefit to the user than the information in this table, it is no longer mentioned.

- *in 3.1 and 3.2, it may be nice to describe explicitly whether it's possible to just use one or the other (proactive vs retroactive)....similar to how in 3.3 it's described how logging can be turned off (or reset). I could envision one wanting to develop without error and then check at the end (retroactive only). Philosophically, I could see that you would not want to build that in and that people could then just load your package at the end...but this may be something explicitly stated in the manuscript.*

Thank you for pointing this out. A comment to this effect has been added to the end of the description of retroactive behavior. 

- *Section 3.2: The average user may not know what the tidyselect helper functions are.  A bit more explanation here would likely help readers/users.*

A short description of tidy select helpers and their applicability here has been added just before the proj_check_some() example.

- *Section 3.4: The average reader may not understand what "and always the dots" means in point 2. Slightly more explanation may be helpful here.* 

The original “and always the dots” mention has been removed and slightly more explanation has been added under item d.

- *Section 3.5.4: the line of code `cat(readChar(install_script, 1e5))` is not intuitive, and that line may benefit from a comment with a brief explanation within the code itself (or in the text above)*

That code has been hidden from view. Instead, there is now a sentence stating that we are looking into the contents of the file.

- *Section 4: Suggestion to rename to future directions or something other than results, given the lack of results here (no fault of the authors, here! simply beyond one's control.) But, I did read and was bummed to see no results here after the section header was Results. Excited to see these results in the future, regardless!*

Agreed on this point. No results are discussed so that warrants a name change. Since the section is about an experiment, however, I have chosen to replace it with “Experimental Testing”. We also decided to run a second trial this semester, so future directions is no longer an applicable name as it is happening currently!

*Very minor* (feel free to ignore)
- *I haven't dug into the code fully so I may have missed it, but I could imagine that a user may want the ability to add their own shim to make a check for something as new packages/functions come out or for something specific to their own uses. Is there functionality for one to create/add their own shim to their installation of fertile?*

Thank you for this excellent idea. There is not currently a functionality for this, but it is definitely something of interest for the future. As a result, we have added it to the future work section.


**Additional Changes**

The first two bullets in the future work section have been completed since the submission of the original manuscript. Due to this, those bullets have been removed and replaced with new future steps.

Additionally, a new bullet point on code commenting (relevant to the has_well_commented_code() function as well as one of the added sources), has been added to the summary of reproducibility components.


