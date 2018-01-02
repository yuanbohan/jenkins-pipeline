Jenkins Pipeline
----------------

GitHub Pull Request Trigger Jenkins Pipeline


## Step

1. add web in GitHub Repo setting page, add the `http(s)://your-jenkins-domain.com/ghprbhook/` and select events.
2. install `GitHub Pull Request Builder` plugin at Jenkins
3. new a pipeline job and check the `GitHub Pull Request Builder`
4. `Pipeline SCM` block, select `Git` and in advanced option fill: 
  - Repositories: `Refspec` : `+refs/pull/*:refs/remotes/origin/pr/*`
  - Branches to build: `Branch Specifier`: `${sha1}`
5. **UNCHECK** `Lightweight checkout`



## Reference

https://github.com/jenkinsci/ghprb-plugin/issues/507
https://wiki.jenkins.io/display/JENKINS/GitHub+pull+request+builder+plugin
