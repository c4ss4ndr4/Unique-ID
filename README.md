Table of Contents\
Unique ID Code\
I.	Metadata Tags\
II.	CSS ID's\
Appendix:


Unique ID Code 
There are many sites produced and hosted by example and prevex. To better identify the example sites that are produced by the former prevex office, a request to define and install a unique identifier on the home html page was suggested. Aside from a unique marker, other information can be included in the identifier, the type of site, the date created, and the casecode can all be added to the marker or the content of the marker, with varying levels of fidelity. 

Careful consideration should be taken to ensure the markers scale with potential legacy sites. 

Background into Semantic Mark-up and DOM Inspection	
The following steps ensure the html mark-up is as standards compliant, ADA compliant and adheres to the DOM standards as accurately as possible.  All suggestions take semantic structure in mind and adhere to strict mark-up guidelines.
Reference:  https://webaim.org/techniques/semanticstructure/

Below are a few suggestions for html tags that can be installed to catalog existing example sites and additional identifier information. 


I.	Metadata Tags

Metadata tags provide additional embedded information used by the browser and search engines, included before the visible body of the page. Primarily they are used for layout and SEO ranking, although much more information can be included in a metadata tag. 

Most widely known and nearly required tag is the document metadata "description" tag and the metadata "viewport" tag. The "description" tag is used by SEO as a website description and the "viewport" tag is used for responsive by setting the browser dimension in relation to the viewport of the screen. Other necessary metatags declare the language, character set, author or content keywords. For purpose of the paper, the metadata tags will refer to the keyword tags.

The first of the following references list all known metadata tag names and their corresponding content. It suggests best nomenclature for independent metadata tags, company name and property. The second of the references is a published Metadata Usage Guide for the company API Shareholic.

Reference WiKi: https://wiki.whatwg.org/wiki/MetaExtensions
Reference GIT HUB: https://github.com/shareaholic/shareaholic-api-docs/blob/master/shareaholic_meta_tags.md

Metadata name tags consist of two parts, the "name" identifier and the "content" identifier. The most commonly known metadata name tag is the name="keyword" identifier used by SEO for tagging, cataloging and searching purposes. In the <meta name="keyword" content="sample text" /> tag, the "content" is filled with relevant descriptive words. At one time keywords were used for SEO ranking, although Google replaced keywords with Page Rank, which take keywords into account but aren't the only element taken into account for search engine optimization. The namespace for the "keyword" metadata tag always uses "keyword" in the name, while the content can be populated with as many keywords as seen fit.  

To add extensibility to both the html meta tag, as well as extend software applications configuration, many APIs use the metadata name tag to define the parameters of their software and extensible options to their applications. These name tags aren't cataloged by search engines and are only visible to the resource provider. Libraries use these tags to add additional references, including links and author information, to their digital books and media collections.  The ones registered with the W3C with current name spaces are also listed on the WiKi Meta Extensions page, https://wiki.whatwg.org/wiki/MetaExtensions. The W3C suggests cross-referencing existing codes and using those codes if appropriate. example IDs need to be unique enough to not be accidentally parsed by another application. If registering the example unique codes with W3C, they also suggest publishing a custom Metadata Usage Guide.

Following the existing metadata naming conventions, the examples below are example suggested meta name and content tags:

Name Tag:
1.	example:claims
2.	example:securities
3.	example:eclaims
4.	example:classview
5.	example:caseview

Content Tag:  	
1.	Casecode
2.	Publish date
3.	Case type
4.	"prevex" or "example"

Or…
Name Tag:\

6.	example:casecode\
7.	example:date\
8.	example:type\
9.	example:producer\
10.	example:author

Content Tag:  

5.	Casecode\
6.	Publish date\
7.	Case type\
8.	"prevex" or "example"\
9.	(author-name)

For example I suggest the following to be added to the <head> of the home page with the following mark-up:\
<meta name="example:typeindentifier" content="example:{casecode}" />\
Or…\
<meta name="example" content="example:{casecode} typeidentifier" />


Example JavaScript code to add a unique metadata tag to the head of the page found in the appendix of the document. Below is a simplified version of the more sophisticated script included in the Appendix.

<body onload="addMeta()">
<script>
        function addMeta() {

            var tagName = document.getElementsByTagName("meta");
            var exampleExists = "false";
            var exampleMeta;
        
            for (var i = 0; i < tagName.length; i++) {

                if (tagName[i].name === "example:claims") {
                    exampleExists = "true";
                    exampleMeta = tagName[i];
                }
            }

            if (exampleExists === "true") {

                var metaContent = exampleMeta.content;
                var amendMeta = metaContent + " " + "example";
                exampleMeta.setAttribute("content", amendMeta);

            } else {

                $("head").append("<meta name='example:claims' content='example' />");

            }
        }
</script>

II.	CSS ID's

In comparison, a CSS ID can be added to the body of the page to uniquely identify it. The simplicity of searching for an ID with JavaScript is appealing, the fidelity of metadata tags increasing the amount of data to be included in the marker.
Example JavaScript to add unique ID to body id CSS selector:


'''<script>
        
	function addId() {
            var t = document.getElementsByTagName("body")[0];
            var newId = "";
            var oldId = "";

            if ($(t).attr("id")) {
                oldId = $(t).attr("id");
                newId = oldId + " " + "example";
                $(t).attr("id", newId);
            } else {
                newId = "example";
                $(t).attr("id", newId);
            }
            
	console.log(newId);
        }        
</script>

	
