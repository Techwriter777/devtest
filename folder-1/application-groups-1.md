# Application Groups

## Introduction

Application groups in Devtron streamline the deployment of microservices by enabling you to build and deploy multiple applications simultaneously. This feature is particularly beneficial when your microservices are interdependent, as a change in one service often triggers the need to redeploy others.

{% hint style="info" %}
Only one application group would exist for each environment. You cannot group applications belonging to different environments.
{% endhint %}

***

## Accessing Application Groups

1.  From the left sidebar, go to **Application Groups**

    ![Figure 1: Application Group (Beta)](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/application-groups/app-group-tab.jpg)
2.  You will get a list of environments. Select the environment to view the application group.

    ![Figure 2: List of Environments](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/application-groups/app-groups.jpg)
3.  The application group would contain the applications meant for deployment in the chosen environment.

    ![Figure 3: Sample Application Group](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/application-groups/app-group-overview.jpg)

As you can see, it has similar options as available under Applications:

* Overview
* Build & Deploy
* Build history
* Deployment history
* Configurations

First, we will walk you through the [key features](broken-reference) of Application Groups, followed by [additional features](broken-reference) that will assist you in performing bulk actions.

***

## Key Features

### Building Images

The **Build & Deploy** tab of your application group helps you trigger the CI build of one or more applications in bulk.

1.  Select the applications using the checkbox and click the **Build Image** button present at the bottom.

    ![Figure 4: Build Option](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/application-groups/select-app.jpg)
2.  The `Build image` screen opens. Select the application and the commit for which you want to trigger the CI build.

    ![Figure 5: Selecting Commit](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/application-groups/select-commit-1.jpg)

    Repeat the step for other applications too and then click **Start Build**.

    ![Figure 6: Building Images](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/application-groups/select-commit-2.jpg)
3.  The build would be initiated, following which, you can close the `Build image` screen.

    ![Figure 7: Triggered Deployment](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/application-groups/build-image.jpg)

### Changing Configurations

The **Configurations** tab of your application group provides you the flexibility to configure the following:

* Deployment template
* ConfigMaps
* Secrets

As shown above, you can handle the configurations of more than one application from a single screen.

![Figure 8: Configurations of each App](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/application-groups/configurations.jpg)

### Deploying Applications

The **Build & Deploy** tab of your application group helps you deploy one or more applications in bulk.

1.  Select the applications using the checkbox and click the **Deploy** button present at the bottom.

    ![Figure 9: Deploy Option](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/application-groups/select-app-deploy.jpg)
2.  Select the application and the CI build for which you want to trigger the deployment.

    ![Figure 10: Selecting Image](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/application-groups/select-image-1.jpg)

    Repeat the step for other applications too and then click **Deploy**.

    ![Figure 11: Deploying Apps](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/application-groups/select-image-2.jpg)
3.  The deployment would be initiated, following which, you can close the screen as shown below.

    ![Figure 12: Triggered Deployment](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/application-groups/deploy-app.jpg)

Once the deployment is successful, the pipelines would show `Succeeded`.

![Figure 13: Successful Deployment](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/application-groups/successful.jpg)

***

## Additional Features

### Filtering Applications

Assume you have multiple applications (maybe 10, 50, 100, or more) showing up in an application group. If you want to restrict your operations (build/deploy/other) to a few applications and not all, the filter feature will help you narrow it down. Thus, you will see only those applications you select from the filter (be it in the `Overview` page, `Build & Deploy` page, and so on.)

1.  Click the filter next to the application group as shown below.

    ![Figure 14: Filter Option](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/application-groups/app-filter-1.jpg)
2.  The filter will show all the applications present in the group. Click to select the relevant ones.

    ![Figure 15: All Apps](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/application-groups/app-filter-2.jpg)
3.  The filter narrows down the list of applications as shown below.

    ![Figure 16: Filtered Apps](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/application-groups/app-filter-3.jpg)
4.  (Optional) If required, you can save the filter for future use by clicking **Save selection as filter**.

    ![Figure 17: Saving a Filter](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/application-groups/save-filter.jpg)
5.  Add a name and description to the filter to help you know its purpose, and click **Save**.

    ![Figure 18a: Naming a Filter](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/application-groups/save-filter-2.jpg)

    ![Figure 18b: Saved Filter](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/application-groups/save-filter-3.jpg)

### Changing Branch

Assume you have a few applications whose build pipelines fetch from the `main` branch of your code repository. However, you decided to maintain a `master` branch henceforth and you want all the upcoming CI builds to consider the `master` branch as the source. Devtron provides you the option to change the branch at both the levels—individual application as well as application group.

1.  In the **Build & Deploy** tab of your application group, select the intended applications, and click the **Change Branch** button present at the bottom.

    ![Figure 19: Changing Branch](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/application-groups/change-branch.jpg)
2.  Enter the new branch name (or the new regular expression if you are using branch regex) and click **Update Branch**.

    ![Figure 20: Updating Branch Name](https://devtron-public-asset.s3.us-east-2.amazonaws.com/images/application-groups/update-branch.jpg)