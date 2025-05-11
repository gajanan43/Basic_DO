# Day-8

1. ✅ Show users with **read, write, and admin** access
2. ✅ List **teams** from the organization that have access to the repository


## 🛠️ **Extended Script: `github-access-report.sh`**

```bash
#!/bin/bash

# GitHub API URL
API_URL="https://api.github.com"

# GitHub username and token (set as environment variables beforehand)
USERNAME="$username"
TOKEN="$token"

# Input repo owner and name
REPO_OWNER=$1
REPO_NAME=$2

if [[ -z "$USERNAME" || -z "$TOKEN" ]]; then
    echo "ERROR: Please export 'username' and 'token' environment variables."
    exit 1
fi

if [[ -z "$REPO_OWNER" || -z "$REPO_NAME" ]]; then
    echo "Usage: $0 <repo_owner> <repo_name>"
    exit 1
fi

function github_api_get {
    local endpoint="$1"
    curl -s -u "$USERNAME:$TOKEN" "$API_URL/$endpoint"
}

echo "=== GitHub Access Report for $REPO_OWNER/$REPO_NAME ==="
echo "Generated on: $(date)"
echo "-----------------------------------------------"

# --- Collaborators by permission ---
function list_collaborators_by_permission {
    echo -e "\n[ Users with Access Permissions]"

    collaborators=$(github_api_get "repos/${REPO_OWNER}/${REPO_NAME}/collaborators?per_page=100")

    echo "Read Access:"
    echo "$collaborators" | jq -r '.[] | select(.permissions.pull == true and .permissions.push == false and .permissions.admin == false) | "  - \(.login)"'
    
    echo "Write Access:"
    echo "$collaborators" | jq -r '.[] | select(.permissions.push == true and .permissions.admin == false) | "  - \(.login)"'

    echo "Admin Access:"
    echo "$collaborators" | jq -r '.[] | select(.permissions.admin == true) | "  - \(.login)"'
}

# --- Team Access (organization only) ---
function list_teams_with_access {
    echo -e "\n[ Teams with Access to Repository]"

    teams=$(github_api_get "repos/${REPO_OWNER}/${REPO_NAME}/teams?per_page=100")

    if [[ $(echo "$teams" | jq length) -eq 0 ]]; then
        echo "No teams have access to this repo."
        return
    fi

    echo "$teams" | jq -r '.[] | "  - \(.name) (Permission: \(.permission))"'
}

# Call functions
list_collaborators_by_permission
list_teams_with_access

echo -e "\n Report Complete"
```

---

## ✅ How to Use

### 1. Set your credentials

```bash
export username="your_github_username"
export token="your_personal_access_token"
```

### 2. Save the script

Save as `github-access-report.sh`

### 3. Make it executable

```bash
chmod 777 github-access-report.sh
```

### 4. Run it

```bash
./github-access-report.sh your-org your-repo
```

---

### 📌 Output Example

```
=== GitHub Access Report for my-org/my-repo ===
Generated on: Sun May 11 13:55:00 IST 2025
-----------------------------------------------

[🧑‍💻 Users with Access Permissions]
Read Access:
  - viewer1
Write Access:
  - developer1
Admin Access:
  - adminuser

[👥 Teams with Access to Repository]
  - DevTeam (Permission: push)
  - Admins (Permission: admin)

✅ Report Complete
```

---

Would you like me to convert this output into a CSV or JSON report for download or automation?
