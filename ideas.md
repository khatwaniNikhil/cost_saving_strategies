1. downscaling
   1. Utilization drop based downscaling dedicated and cross cutting infra
   2. Scheduled shutdown
2. Traffic 
   1. Restrict traffic to Single AZ 
4. Disable use of decaptcha service 
5. S3
   1. Purge data older basis usage 
   2. delete incomplete multipart uploads
   3. S3 pre-signed urls (valid for 24 hours) for exports
   4. Setup cost per bucket tags
      1. https://aws.amazon.com/premiumsupport/knowledge-center/s3-find-bucket-cost 
      2. https://www.powerupcloud.com/aws-bulk-tagging-tool-aws-tagger-part-1/"
   5. S3 data cleanup
      1. unwanted files using lifecycle policy (older than x days), 
      2. delete incomplete multipart uploads (uniware mysql and mongo backups)
         1. https://github.com/rubrikinc/find-incomplete-s3-multipart-uploads
         2. https://gist.github.com/mchv/9dccbd9245287b26e34ab78bad43ea6c
         3. https://aws.amazon.com/blogs/aws/s3-lifecycle-management-update-support-for-multipart-uploads-and-delete-markers/
         4. https://gist.github.com/mchv/9dccbd9245287b26e34ab78bad43ea6c
         5. https://wasabi-support.zendesk.com/hc/en-us/articles/360033859411-How-do-I-clean-up-my-failed-multipart-uploads-
   6. archival using S3 Glacier and S3 Glacier Deep Archive "
   7. S3 storage tier revisit
      1. RRS not recommended and looks like phased out(refer 
         1. https: //www.lastweekinaws.com/blog/s3-reduced-redundancy-storage-is-dead/), 
         2. https://mysteriouscode.io/blog/aws-s3-storage-classes-pricing-is-not-what-you-think/
      2. choice should be between Standard Infrequent Access and One Zone Infrequent Access (no cross AZ replication)
         1. https://www.concurrencylabs.com/blog/save-money-using-s3-infrequent-access/
      3. caveats
         1. as percentage of data accessed from Infrequent Access area increases, cost savings turns south
         2. standard to infrequent access conversion charge
         3. minimum billable object size of 128KB...crosscheck majority stored file size
6. Partially disable cloudwatch, guardduty
