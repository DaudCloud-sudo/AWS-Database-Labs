# AWS-Database-Labs

# Setting Up the Database with DynamoDB

In this lab, my responsibility is to keep the employee database up to date. I'll start by launching another EC2 instance and then create a DynamoDB table for the employee directory application.

## Table of Contents
- [Task 1: Launching an EC2 Instance](#task-1-launching-an-ec2-instance)
- [Task 2: Creating the DynamoDB Table](#task-2-creating-the-dynamodb-table)
- [Task 3: Testing the Application](#task-3-testing-the-application)
- [Task 4: Viewing the Item in the Database](#task-4-viewing-the-item-in-the-database)
- [Task 5: Stopping Your EC2 Instance](#task-5-stopping-your-ec2-instance)

---

## Task 1: Launching an EC2 Instance

Note: For detailed EC2 setup instructions, please refer to [AWS Compute Labs](https://github.com/DaudCloud-sudo/AWS-Compute-Labs).

1. Log in to the AWS Management Console with your Admin user.
2. Open the Amazon EC2 console by searching for **EC2**.
3. In the navigation pane, choose **Instances**.
4. If needed, select the check box for the `employee-directory-app-s3` instance, which should be in the **Stopped** state.
5. Choose **Actions** > **Image and templates** > **Launch more like this**.
6. For **Name**, append `-dbms` to the value.

    **Example:**
    ```
    employee-directory-app-dbms
    ```

7. For **Key pair name**, select **app-key-pair**.
8. Under **Network settings** and **Auto-assign Public IP**, choose **Enable**.
9. Choose **Launch instance**.
10. Choose **View all instances**.
11. The instance should now appear in the **Instances** list.
12. Wait for the **Instance state** to change to **Running** and the **Status check** to change to **2/2 checks passed**.

![image](https://github.com/user-attachments/assets/158d9358-a790-4548-a702-182761df4fdb)

14. If needed, clear the check box for the `employee-directory-app-s3` instance.
15. Select the check box for `employee-directory-app-dbms`.
16. Copy the **Public IPv4 address**.

    > **Note:** Make sure that you only copy the address instead of choosing the open address link.

17. In a new browser window, paste the IP address that you copied. Make sure to remove the `S` after `HTTP` so you are using only `HTTP` instead.
18. You should see an **Employee Directory** placeholder. The application won't be fully functional yet because it is not connected to a database.
19. Close the application browser window.

## Task 2: Creating the DynamoDB Table

To connect the application to a database, you first need to create one using DynamoDB.

1. Return to the AWS Management Console, and search for **DynamoDB**.
2. In the navigation pane, choose **Tables**.
3. Choose **Create table** and configure the following settings:
    - **Table name**: `Employees`
    - **Partition key**: `id`
4. Choose **Create table**.

![image](https://github.com/user-attachments/assets/31e6dce9-e474-4648-be35-a4ebaf90cb17)

## Task 3: Testing the Application

1. Return to the Amazon EC2 console by searching for and opening **EC2**.
2. In the **Instances** list, select the check box for the `employee-directory-app-dbms` instance.
3. On the **Details** tab, copy the **Public IPv4 address** and paste it into a new browser window.
4. In the application interface, choose **Add**.
5. Create a new employee entry by entering a name, location, job title, and selecting some attributes.
6. Upload a picture by choosing **Browse** and selecting a photo from your computer.
7. Choose **Save**.
8. Create and save a few more employee entries.

    > **Note:** You can also edit and delete entries.

9. In the employee directory application, you should now see the list of employees (and their photos) that you added.

![image](https://github.com/user-attachments/assets/25246413-b241-4438-ba52-7ebe75e87ebf)

## Task 4: Viewing the Item in the Database

1. Return to the AWS Management Console, and search for **DynamoDB**.
2. In the navigation pane, choose **Tables**.
3. Open the table details by choosing the **Employees** link.
4. Choose **Explore table items**.
5. In the **Items returned** list, you should now see the entries in the database that you made using the application on the EC2 instance.

![image](https://github.com/user-attachments/assets/507ee3a9-a63f-4ede-a3d4-a730c6d833f1)

## Task 5: Stopping Your EC2 Instance

To prevent future costs, you will now stop the instance.

> **Note:** Do not terminate the instance because you will use it in the next exercise.

1. Return to the Amazon EC2 console by searching for and opening **EC2**.
2. In the navigation pane, choose **Instances** if needed.
3. Select the check box for `employee-directory-app-exercise6`.
4. Choose **Instance state** > **Stop instance**.
5. In the dialog box, choose **Stop**.
6. The **Instance state** will eventually change to **Stopped**.

---

Note: This guide is part of the AWS SAA preparation course lab. Ensure you terminate all resources to avoid incurring costs.
