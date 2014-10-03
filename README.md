TYPO3 Neos Sitemap Plugin
=========================

This plugin provides a typoscript-based plugin for TYPO3 Neos sitemap handling.

Note: this package is still experimental and may change heavily in the near future.
Note: this plugin as only be tested on Neos 1.2 (dev-master), with some patch currently under review.

Quick start
-----------
* check the file `beard.json` and cherry-pick all the required patches

* include the Plugin's route definitions to your `Routes.yaml` file, just like:

```yaml
-
  name: 'FlowpackPluginSitemap'
  uriPattern: '<FlowpackPluginSitemapSubroutes>'
  subRoutes:
    FlowpackPluginSitemapSubroutes:
      package: Flowpack.Plugin.Sitemap
      variables:
        'sitemapBaseUri': ''
        'rootNodePath': '/sites/officialwebsite'
```

* The `rootNodePath` variable must contain the root node path of your website. 

* The `sitemapBaseUri` is the prefix of your sitemap.xml, leave it empty to have http://domain.com/sitemap.xml.

* open your browser to http://domain.com/sitemap.xml to check your site map

TypoScript Configuration
------------------------

The sitemap rendering is based on the TypoScript Menu prototype, so can use any property from this prototype:

```
prototype(Flowpack.Plugin.Sitemap:GoogleSiteMap) < prototype(TYPO3.TypoScript:Http.Message) {
	urlset {
		maximumLevels = 10
		renderHiddenInIndex = FALSE
	}
}
```