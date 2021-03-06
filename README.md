Firebase Jekyll Comments
======================

[Jekyll](http://jekyllrb.com/) is the coolest static-everything blogging platform out there, but if you came from a more dynamic blogging platform, you probably miss comments. I know I do. 

### Unsocial Blogging
![unsocial blogging](docs/forever-alone.png)

### The Realtime Solution
![firebase jekyll](docs/firebase-jekyll.png)

Anyway, here's a handy dandy include for Jekyll that adds real time comments to your blog without any backend code. The backend part is handled by [Firebase](https://firebase.com)

Interested? Check out a [live demo](https://jekyll-comments-demo.firebaseapp.com).

## Setup

1. Create a [new Firebase](https://www.firebase.com/account/) for your blog comments.
1. Copy the files from [_includes](_includes) into the `_includes` folder in
   the root of your blog. Create the directory if it does not already exist.
2. Edit your `_config.yaml` and specify `fbc-comments-firebase`, the URL of the Firebase to host your comments, e.g.
   https://jekyll-comments-demo.firebaseio.com/
4. [`_includes/firebase-comment-form-template.html`](_includes/firebase-comment-form-template.html) represents your
   comments form. Edit it to match your blog.
   - Use the same markup as the rest of your blog. Jekyll interprets it like any other include at build time. 
   - Preserve the `fbc-*` element ids and `data-auth-provider` attributes. They are required by the plugin to function.
5. [`_includes/firebase-comment-template.html`](_includes/firebase-comment-template.html) represents an individual
   comment. Edit it to match your blog.
   - Use the same markup as the rest of your blog. Jekyll interprets it like any other include at build time.
   - It is further processed with a JavaScript template engine at the time of rendering. Use these template tags:
       - `<%=link %>` - Commenter's profile URL
       - `<%=picture %>` - The beautiful mug shot of your commenter
       - `<%=displayName %>` - Their name
       - `<%=comment %>` - What they said about your stuff
6. Enable SimpleLogin and add API keys and secrets to forge for
   [Facebook](https://www.firebase.com/docs/web/guide/simple-login/facebook.html),
   [Twitter](https://www.firebase.com/docs/web/guide/simple-login/twitter.html),
   [GitHub](https://www.firebase.com/docs/web/guide/simple-login/github.html), and
   [Google](https://www.firebase.com/docs/web/guide/simple-login/google.html).
1. Paste the contents of [`firebase-security-rules.json`](firebase-security-rules.json) into the
   [security rules](https://www.firebase.com/docs/security/guide.html) pane for your Firebase, or edit `firebase.json`
   to deploy them to [Firebase Hosting](https://www.firebase.com/docs/hosting/).

7. Add the include to the appropriate layout files.

        {% include firebase-comments.ext %}

8. Deploy your blog, share your posts with your friends, and watch the comments arrive in real time.
