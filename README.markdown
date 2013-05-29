Multilingual Entry URL
======================

The multilingual version of the entry url field.


## 1 About ##

When adding this field to a section, the following options are available to you:

* **Anchor Label** is the text used for the hyperlink in the backend
* **Anchor URL** is the URL of your entry view page on the frontend. An `<entry id="123">...</entry>` nodeset is provided from which you can grab field values, just as you would from a datasource. For example:

		{entry/title/item[@lang='$language_code']}

* **For `Multilingual Text`**, you can use `$language_code` (without `{}`) as a placeholder for language codes. It will be replaced for each language on URL generation.<br />
Let's say my `Articles` Section with a `Multilingual text` field called `Title`. Given an `Articles` Page with an URL param pointing to `Title`, an expression like this must be used:

		/articles/{entry/title/item[@lang='$language_code']/@handle}/   --> make sure you know the XML output of Multilingual Text

* **Open links in a new window** enforces the hyperlink to spawn a new tab/window
* **Hide this field on publish page** hides the hyperlink in the entry edit form

### Datasource Support ###

Datasource support has been added via the config. 
No Options in backend exists yet; however this shall be added in the future. 
Currently just find the `MULTILINGUAL_ENTRY_URL` block in the config and add the datasources in a comma-separated list.

	'datasources' => 'datasource1,datasource2,datasource3',

### XSLT Support ###

In the latest update XSLT Support was added, allowing you to define a relative path to your `xsl` file which will be executed instead of the xpath query.
For example:

	/entry-url/articles.xsl

Note that the path can be anything under workspace, entry-url was used for separation. Your template has to match `/` to work.

### Note about compatibility ###

Currently the URL is generated this way:

    /__LANGUAGE-CODE__/URL

However if you have the [Domain Language Redirect](https://github.com/jonmifsud/domain_language_redirect) enabled; 
the extension will prepend output with the domain set in the Domain Redirect Extension


## 2 Installation ##
 
1. Upload the 'multilingual_entry_url' folder in this archive to your Symphony 'extensions' folder.
2. Enable it by selecting the "Field: Multilingual Entry URL", choose Enable from the with-selected menu, then click Apply.
3. The field will be available in the list when creating a Section.
