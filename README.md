# compress and decompress

for compress large database file into each chunk, use `tar cvzf - dep_network_npm_search.db | split --bytes=80MB - dep_network_npm_search.db.tar.gz.`

for decompress files into one, use `cat dep_network_npm_search.db.tar.gz.a* | tar xzvf -`

# 

In previous related works and studies on NPM packages, researchers used https://registry.npmjs.org/-/all to obtain latest public npm packages list. However, based on https://blog.npmjs.org/post/157615772423/deprecating-the-all-registry-endpoint, NPM has deprecated and shut down this public API due to the dramastically increasing size of packages hosted in NPM registry.

Luckily I found a work around to obtain a similar list of public NPM packages list from an alternative official website, replicate registry hosted on couchDB.

To obtain only the list of name:
curl https://replicate.npmjs.com/_all_docs -o replicate_npm_all_doc.json

If with docs information, which is identical to the package.jsonfiles in each package, included:
curl https://replicate.npmjs.com/_all_docs?include_docs=true -o replicate_npm_all_doc_include_true


