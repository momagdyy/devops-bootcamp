## What is Role-based Authorization?
Controls who can do what in Jenkins.
Different users get different permissions.

## Steps:

### 1. Install Plugin:
- Install Role-based Authorization Strategy plugin

### 2. Enable Role-based Authorization:
- Manage Jenkins → Security
- Select Role-Based Strategy

### 3. Create Roles:
- admin role: All permissions
- read-only role: Overall/Job/View Read only

### 4. Create Users:
- user1: admin role
- user2: read-only role

### 5. Assign Roles:
- Manage and Assign Roles → Assign Roles
- user1 → admin
- user2 → read-only

## Result:
- user1: Full admin access 
- user2: Read only access 
- user2 cannot create/delete/manage 