<div align="center">
	<img width="900" src="https://github.com/CCTSAI-Tony/GitHubSocial/blob/master/logo.png" alt="GitHubSocial">
	<br>
</div>

This web app let you connect to other developer's github profile, create your own profile page and share posts to others.[LINK](https://polar-depths-16631.herokuapp.com/).

I'm happy to accept more configurability and features. PR welcome! What you see here is just what I needed for my own apps.

## User Interfaces

#### Main site - login

<img src="https://github.com/CCTSAI-Tony/GitHubSocial/blob/master/login" width="532">

#### Dashboard

## <img src="https://github.com/CCTSAI-Tony/GitHubSocial/blob/master/dashboard.png" width="532">

#### Profiles

## <img src="https://github.com/CCTSAI-Tony/GitHubSocial/blob/master/profiles.png" width="532">

#### Developers

## <img src="https://github.com/CCTSAI-Tony/GitHubSocial/blob/master/developers.png" width="532">

#### Posts

## <img src="https://github.com/CCTSAI-Tony/GitHubSocial/blob/master/post.png" width="532">

# Quick Start 🚀

### Add a default.json file in config folder with the following

```
{
  "mongoURI": "<your_mongoDB_Atlas_uri_with_credentials>",
  "jwtSecret": "secret",
  "githubToken": "<yoursecrectaccesstoken>"
}
```

### Install server dependencies

```bash
npm install
```

### Install client dependencies

```bash
cd client
npm install
```

### Run both Express & React from root

```bash
npm run dev
```

### Build for production

```bash
cd client
npm run build
```

### Test production before deploy

After running a build in the client 👆, cd into the root of the project.  
And run...

```bash
NODE_ENV=production node server.js
```

Check in browser on [http://localhost:5000/](http://localhost:5000/)

### Deploy to Heroku

If you followed the sensible advice above and included `config/default.json` `and config/production.json` in your .gitignore file, then pushing to Heroku will omit your config files from the push.  
However, Heroku needs these files for a successful build.  
So how to get them to Heroku without commiting them to GitHub?

What I suggest you do is create a local only branch, lets call it _production_.

```bash
git checkout -b production
```

We can use this branch to deploy from, with our config files.

Add the config file...

```bash
git add -f config/production.json
```

This will track the file in git on this branch only. **DON'T PUSH THE PRODUCTION BRANCH TO GITHUB**

Commit...

```bash
git commit -m 'ready to deploy'
```

Create your Heroku project

```bash
heroku create
```

And push the local production branch to the remote heroku master branch.

```bash
git push heroku production:master
```

Now Heroku will have the config it needs to build the project.

> **Don't forget to make sure your production database is not whitelisted in MongoDB Atlas, otherwise the database connection will fail and your app will crash.**

After deployment you can delete the production branch if you like.

```bash
git checkout master
git branch -D production
```

Or you can leave it to merge and push updates from another branch.  
Make any changes you need on your master branch and merge those into your production branch.

```bash
git checkout production
git merge master
```

Once merged you can push to heroku as above and your site will rebuild and be updated.

---

### License

This project is licensed under the MIT License
