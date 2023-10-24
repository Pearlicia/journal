I still remember a curious case around one year back! 🤔

The client has so many accounts, especially test , staging , qa, pre-prod, prod!

Now the problem is there are all team teams building and testing images manually!

They suddenly started facing one issue that their EKS cluster not able to pull image and giving ImagePullBackOff error but the nodes have all the necessery access to pull images from ECR , so get to know about me from one of their employee and hired me!


Can you guess what was the issue and how I had fixed the issue?

Yes, I too first checked the IAM policies set for nodes , it was easy as they used Terraform to create clusters and resources!

I saw all fine in the IAM policies, I did assume the same role to test able to pull image or not, that worked too!

I got a hunch from their multi account scanaio , so started investigating their k8s manifest files and found in the image url the account id is different than when I am making sts call to verify the current account id of the assumed role! that's it , that was the root cause, change image path to proper ecr image uri!

now that would just be a path, to fix this issue permanently, suggested them to automate the k8s yaml generation dynamically, suggested either kustomize or helm templates, and since most of the team is skilled in helm, so used helm templating to dynamically generate and update k8s templates via CI pipeline itself!

Now, my curiosity, if you were in my place, how would you have done it differently?
