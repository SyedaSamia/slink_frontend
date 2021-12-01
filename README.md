# SLINK URL Shortener Frontend

This is the frontend for the URL Shortener service 'Slink'. The demo is available at https://s-link.netlify.app/. 

The frontend is done in VueJS and Quasar and the database is MongoDB NoSQL DB.

The implementation for the backend can be found here https://github.com/SyedaSamia/slink_backend

![Screenshot](/images/slink.png)

## Capabilities

A user can enter an arbitrary URL "X" on the website and get a shortened URL in return.

On visiting the shortened URL, the user gets redirected to “X".

The shortening has to be idempotent, i.e. a given URL always has to yield the same short URL as a result.

On the website, the user can also see stats for all shortUrls that have been generated (by anyone) on the site:
  For each shortUrl, how often did someone attempt to shorten that specific URL?
  For each shortUrl, how often was it visited?

## Project Architecture

The architecture for the project is depicted in the following diagrams. 

![Screenshot](/images/architecture.png)
![Screenshot](/images/architecture2.png)



## Project setup as per VueJS Documentation
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
