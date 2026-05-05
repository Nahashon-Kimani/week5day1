## Step 1: Delete the Amazon RDS Database Instance

1. In RDS, select your instance.
2. Click "Actions" > "Delete".
3. **Uncheck** "Create final snapshot" if not needed.
4. Type "delete me" to confirm.
5. Click "Delete".

**Note**: 
If Enable deletion protection is **Checked**, uncheck it click **Continue**


## Step 2: Delete the Amazon EC2 instance
1. Select the EC2 instance instance.
2. Select **Instance State** then **Terminate(delete) instance**

## Step 3: Delete the Auto Scaling Group
*Reference: See auto-scaling.md for Auto Scaling Group creation details.*

1. Go to **EC2 > Auto Scaling > Auto Scaling Groups**.
2. Select your Auto Scaling group.
3. Click **Delete**.
4. In the confirmation dialog, select **Delete instances** to terminate instances created by the ASG.
5. Click **Delete** to confirm.
6. Wait for the ASG and its instances to be fully terminated.

## Step 4: Delete the Application Load Balancer
*Reference: See auto-scaling.md for ALB creation details.*

1. Go to **EC2 > Load Balancing > Load Balancers**.
2. Select your Application Load Balancer (ALB).
3. Click **Actions** > **Delete load balancer**.
4. In the confirmation dialog, click **Yes, delete**.
5. Wait for the ALB to be fully deleted.

## Step 5: Delete the Target Group
*Reference: See auto-scaling.md for Target Group creation details.*

1. Go to **EC2 > Load Balancing > Target Groups**.
2. Select your Target Group.
3. Click **Actions** > **Delete**.
4. In the confirmation dialog, click **Yes, delete**.

## Step 6: Delete the Launch Template
*Reference: See auto-scaling.md for Launch Template creation details.*

1. Go to **EC2 > Instances > Launch Templates**.
2. Select your Launch Template.
3. Click **Actions** > **Delete launch template**.
4. In the confirmation dialog, click **Delete**.

## Step 7: Delete the CloudFront Distribution
*Reference: See task.md for CloudFront distribution creation details.*

1. Go to **CloudFront > Distributions**.
2. Select your CloudFront distribution.
3. First, you must **disable** the distribution before deletion:
   - Click on the distribution ID to open its settings.
   - Click the **Disable** button.
   - In the confirmation dialog, click **Disable**.
   - Wait for the distribution status to change from "Enabled" to "Disabled" (this may take a few minutes).
4. Once the distribution is **Disabled**, select it again.
5. Click **Delete** button.
6. In the confirmation dialog, click **Delete** to confirm deletion.
7. Wait for the distribution to be fully removed (it will disappear from the list).

**Note**: CloudFront distributions must be disabled before they can be deleted. This is a safety measure to prevent accidental deletion of active distributions.


