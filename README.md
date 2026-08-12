# Microsoft Entra ID — Group Management Lab

This lab covers common **Microsoft Entra ID group-management tasks**, including creating Microsoft 365 and security groups, managing group membership, assigning group owners, and assigning licenses to groups.

> **Prerequisites**
>
> * Access to a Microsoft Entra tenant.
> * Appropriate administrative permissions to create and manage groups.
> * Access to the [Microsoft Entra admin center](https://entra.microsoft.com/).
> * Access to the [Microsoft 365 admin center](https://admin.microsoft.com/).
> * The users referenced in this lab, including **Bhogeswar Kalita** and **External User**, should already exist in the tenant.

---

# Task 1 — Create a Microsoft 365 Group

In this task, you will create a Microsoft 365 group named **Project23** and add **Bhogeswar Kalita** as a member.

### 1. Open Microsoft Entra Admin Center

1. Open the [Microsoft Entra admin center](https://entra.microsoft.com/).
2. Sign in using your tenant administrator credentials.
3. From the left-hand navigation pane, select **Groups** → **All groups**.
4. Select **+ New group**.

### 2. Configure the Group

Enter the following values:

| Field                 | Value                                                                                      |
| --------------------- | ------------------------------------------------------------------------------------------ |
| **Group type**        | `Microsoft 365`                                                                            |
| **Group name**        | `Project23`                                                                                |
| **Group description** | `This group consists of members of the new AI Simulation software with codename Project23` |
| **Membership type**   | `Assigned`                                                                                 |

### 3. Add a Member

1. Under **Members**, select **No member selected**.
2. Find and select **Bhogeswar Kalita**.
3. Select **Select**.
4. Review the group configuration.
5. Select **Create**.

> **Result:** The **Project23** Microsoft 365 group is created with **Bhogeswar Kalita** as a member.

---

# Task 2 — Create a Security Group

In this task, you will create a **dynamic security group** that automatically includes all guest users in the tenant.

### 1. Create the Group

1. Open the [Microsoft Entra admin center](https://entra.microsoft.com/).
2. Sign in using your tenant administrator credentials.
3. From the left-hand navigation pane, select **Groups** → **All groups**.
4. Select **+ New group**.

Configure the group as follows:

| Field                 | Value                                                         |
| --------------------- | ------------------------------------------------------------- |
| **Group type**        | `Security`                                                    |
| **Group name**        | `Guest Users`                                                 |
| **Group description** | `This group has all the Guest users currently in the tenant.` |
| **Membership type**   | `Dynamic User`                                                |

### 2. Configure the Dynamic Membership Rule

1. Under **Dynamic user members**, select **Add dynamic query**.
2. Configure the query using the following values:

| Field        | Value      |
| ------------ | ---------- |
| **Property** | `userType` |
| **Operator** | `Equals`   |
| **Value**    | `Guest`    |

3. Save the dynamic membership rule.
4. Select **Create**.

> **Note:** Dynamic group membership is not necessarily populated immediately. Allow a few minutes for Microsoft Entra ID to evaluate the rule and populate the group.

### 3. Verify Group Membership

1. Return to **Groups** → **All groups**.
2. Select **Refresh**.
3. Select the **Guest Users** group.
4. Select **Members**.
5. Verify that guest users are being added to the group.

> **Result:** The **Guest Users** security group automatically contains users whose `userType` is `Guest`.

---

# Task 3 — Add an Existing User to a Group

In this task, you will add **External User** to the **Project23** group.

### Method 1 — Add the User from the Group

1. Open the [Microsoft Entra admin center](https://entra.microsoft.com/).
2. Sign in using your tenant administrator credentials.
3. Select **Groups** → **All groups**.
4. Select the **Project23** group.
5. Select **Members**.
6. Select **+ Add members**.
7. Find **External User**.
8. Select the checkbox next to the user.
9. Select **Select**.

> **Result:** **External User** is now a member of **Project23**.

---

## Subtask 1 — Alternative Method: Add a Group Membership from the User

You can also add a user to a group from the user's profile.

1. From the left-hand navigation pane, select **Users** → **All users**.
2. Find and select **External User**.
3. Select **Groups**.
4. Select **+ Add memberships**.
5. Select the group you want to add the user to.
6. Select **Select**.

> **Tip:** Both approaches produce the same result. Use the group-based method when managing memberships for a specific group, and the user-based method when managing a user's memberships.

---

# Task 4 — Add Owners and Licenses to a Group

In this task, you will add **Bhogeswar Kalita** as an owner of the **Project23** group.

## Part 1 — Add a Group Owner

1. Open the [Microsoft Entra admin center](https://entra.microsoft.com/).
2. Sign in using your tenant administrator credentials.
3. Select **Groups** → **All groups**.
4. Select the **Project23** group.
5. Select **Owners**.

> **Note:** Depending on your tenant configuration, the administrator who creates a group may automatically become an owner if no other owner is specified.

6. Select **+ Add owners**.
7. Find and select **Bhogeswar Kalita**.
8. Select **Select**.
9. Verify that **Bhogeswar Kalita** now appears in the group's list of owners.

> **Result:** Bhogeswar Kalita is now an owner of the **Project23** group.

---

## Subtask 1 — Assign a License to a Group

You can assign certain Microsoft licenses to a group so that eligible users receive the license through group-based licensing.

### 1. Open Microsoft 365 Admin Center

1. Open a new browser tab.
2. Open the [Microsoft 365 admin center](https://admin.microsoft.com/).
3. Sign in using your tenant administrator credentials if prompted.

### 2. Select the License

1. From the left-hand navigation pane, open **Billing**.
2. Select **Licenses**.
3. Select **Microsoft Power Automate Free**.
4. Select the **Groups** tab.
5. Select **+ Assign licenses**.

### 3. Assign the License

1. Use the group selector on the right side of the page.
2. Select the **Project23** group.
3. Select **Assign**.
4. Verify the confirmation notification indicating that the license was successfully assigned.
5. Close the confirmation notification.
6. Select **Refresh** to verify the group license assignment.

> **Result:** The **Project23** group has been assigned the **Microsoft Power Automate Free** license.

---

# Lab Summary

By completing this lab, you have practiced the following Microsoft Entra ID group-management operations:

| Task                 | Skill                           |
| -------------------- | ------------------------------- |
| **Task 1**           | Create a Microsoft 365 group    |
| **Task 2**           | Create a dynamic security group |
| **Task 3**           | Add users to an existing group  |
| **Task 4**           | Add group owners                |
| **Task 4 — Subtask** | Assign a license to a group     |

## Key Concepts

* **Microsoft 365 groups** provide collaboration capabilities across Microsoft 365 services.
* **Security groups** can be used to control access to resources and services.
* **Dynamic membership** automatically adds or removes users based on defined rules.
* **Group owners** can help manage group membership and configuration.
* **Group-based licensing** allows licenses to be assigned to a group rather than individually to users.
* Dynamic membership changes may take some time to be reflected in the group.
