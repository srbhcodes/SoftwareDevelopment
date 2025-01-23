### Step-by-Step Guide to Setting Up GitHub with WSL (Ubuntu) via SSH

---

#### **1. Install Git on WSL (Ubuntu)**

1. Open your WSL terminal.
2. Update the package list:

   ```bash
   sudo apt update
   ```

3. Install Git:

   ```bash
   sudo apt install git
   ```

---

#### **2. Set Up SSH Key**

If you don’t already have an SSH key, generate one for authentication with GitHub.

##### **Generate an SSH Key**

1. Run the following command, replacing `your_email@example.com` with your GitHub email:

   ```bash
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```

2. Press `Enter` to accept the default file location.
3. (Optional) Enter a passphrase for added security and confirm it.

##### **Add the SSH Key to the SSH Agent**

1. Ensure the SSH agent is running:

   ```bash
   eval "$(ssh-agent -s)"
   ```

2. Add your SSH private key to the agent:

   ```bash
   ssh-add ~/.ssh/id_ed25519
   ```

---

#### **3. Add the SSH Key to GitHub**

1. Copy the SSH public key to your clipboard:

   ```bash
   cat ~/.ssh/id_ed25519.pub
   ```

2. Go to [GitHub SSH settings](https://github.com/settings/keys).
3. Click **New SSH Key**.
4. Paste the copied SSH key into the "Key" field.
5. Add a title (e.g., "WSL Ubuntu").
6. Click **Add SSH key**.

---

#### **4. Test SSH Connection to GitHub**

1. Verify the connection by running:

   ```bash
   ssh -T git@github.com
   ```

2. You should see:

   ```
   Hi username! You've successfully authenticated, but GitHub does not provide shell access.
   ```

---

#### **5. Configure Git (if not already done)**

1. Set your user name:

   ```bash
   git config --global user.name "Your Name"
   ```

2. Set your email:

   ```bash
   git config --global user.email "your_email@example.com"
   ```

---

#### **6. Initialize a Git Repository**

1. Navigate to your project directory:

   ```bash
   cd /path/to/your/project
   ```

2. Initialize Git:

   ```bash
   git init
   ```

---

#### **7. Stage Files for Commit**

1. Add all files to the staging area:

   ```bash
   git add .
   ```

---

#### **8. Commit the Changes**

1. Commit the staged files with a meaningful message:

   ```bash
   git commit -m "Initial commit"
   ```

---

#### **9. Add a Remote Repository**

1. If you don’t have a remote repository already linked, add it:

   ```bash
   git remote add origin git@github.com:yourusername/repository-name.git
   ```

---

#### **10. Change the Remote URL (Optional)**

1. To update the remote URL, run:

   ```bash
   git remote set-url origin git@github.com:yourusername/new-repository-name.git
   ```

---

#### **11. Push the Changes to GitHub**

1. Rename the default branch to `main` (if needed):

   ```bash
   git branch -M main
   ```

2. Push the project to GitHub:

   ```bash
   git push -u origin main
   ```

---

#### **12. Check the Remote Repository URL**

1. Confirm the correct remote URL is set:

   ```bash
   git remote -v
   ```

   The output should display something like:

   ```
   origin  git@github.com:yourusername/repository-name.git (fetch)
   origin  git@github.com:yourusername/repository-name.git (push)
   ```

---

Following these steps ensures GitHub is fully set up with WSL Ubuntu via SSH!
