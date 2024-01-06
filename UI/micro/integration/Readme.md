#Implementing Module Federation
1. Designate one app as the Host(CONTAINER) and one as the Remote(PRODUCTS).
1. In the Remote, decide which modules (files) you want to make available to other projects.
1. Set up Module Federation plugin to expose those files.
1. In the Host, decide which files you want to get from the remote.
1. Set up Module Federation plugin to fetch those files.
1. In the Host, Refactor the entry point to load asynchronously.
1. In the Host, import whatever files you need from the remote.
