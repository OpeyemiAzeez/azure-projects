# 04: Configure Conditional Access Policies

This section outlines the steps to configure Conditional Access (CA) policies to enforce secure access to Azure resources.

## Step 1: Sign In to Azure Portal

1. Navigate to [https://portal.azure.com](https://portal.azure.com).
2. Use an account with appropriate permissions (e.g., Security Administrator or Global Administrator).

## Step 2: Access Conditional Access

1. In the search bar, type **Conditional Access** and select it.
2. From the left pane, click on **Policies**.

## Step 3: Create a New Policy

1. Click **+ New policy**.
2. Enter a name for your policy (e.g., `Require MFA for all users`).

## Step 4: Assign Users or Groups

1. Under **Assignments > Users**, click **Select users and groups**.
2. Choose specific users or a group (e.g., `Admins`).

## Step 5: Configure Cloud Apps or Actions

1. Under **Assignments > Cloud apps or actions**, choose:
   - **Select apps** → Pick apps like `Microsoft Office 365` or `All cloud apps`.

## Step 6: Set Conditions (Optional)

- You can define conditions like:
  - **Sign-in risk**
  - **Device platform**
  - **Locations**

## Step 7: Grant Controls

1. Under **Access controls > Grant**, select:
   - ✅ **Require multi-factor authentication**
2. Click **Select**.

## Step 8: Enable and Create Policy

1. Under **Enable policy**, set it to **On**.
2. Click **Create**.

## ✅ Result

Once created, the Conditional Access policy will enforce MFA or other rules for users trying to access defined apps or services.

---

## 🔒 Best Practices

- Test with a small group before wide rollout.
- Use **report-only mode** to simulate effects.
- Combine CA with Identity Protection (if licensed).

---

## 📸 Screenshots

![Create Conditional Access Policy](images/conditional-access-policy.png)

![Grant MFA Requirement](images/conditional-access-mfa.png)
