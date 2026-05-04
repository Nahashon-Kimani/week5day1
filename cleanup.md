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