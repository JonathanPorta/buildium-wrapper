### buildium-wrapper
The plan was to somehow wrap the buildium tenant site and show it on a private domain, but, due to the way buildium works, it doesn't seem possible at this time.

These file do a JS redirect.

However, better luck/performance/everything can be had by simply doing this:

https://www.dropbox.com/s/ni8camysnfk5umx/Screenshot%202017-07-13%2007.05.08.png?dl=0

### Current Setup/Configuration
In case I forget...again...

#### Cloudflare
We point to three CNAME records on gatsby.ventures to S3 buckets that have static site hosting enabled.

[Cloudflare Screenshot!](https://www.dropbox.com/s/uqjj60qcna4x73o/Screenshot%202017-07-13%2007.32.54.png?dl=0)

- buildium.gatsby.ventures CNAMES to buildium.gatsby.ventures.s3-website-us-west-2.amazonaws.com (there was a type previously... No Gastby'ing!)
- rentals.gatsby.ventures CNAMES to rentals.gatsby.ventures.s3-website-us-west-2.amazonaws.com
- gatsby.ventures CNAMES to gatsby.ventures.s3-website-us-west-2.amazonaws.com

#### S3 Bucket Madness
- arn:aws:s3:::buildium.gatsby.ventures redirects to https://gatsbyventures.managebuilding.com/Manager/PublicPages/Login.aspx
- arn:aws:s3:::rentals.gatsby.ventures redirects to https://gatsbyventures.managebuilding.com/Resident/public/home
- arn:aws:s3:::gatsby.ventures redirects to rentals.gatsby.ventures (tried to get it to use the "redirect to bucket" feature, but, using the target bucket's ARN ID thingy didn't work. Plus, there was no way to selection a container. I think a dropown of your containers with Everyone Read perms would be balla'.)

### JavaScript redirects
You can see some amazing JS based redirects if you run `make local` and then visit [localhost:8000](http://localhost:8000)
