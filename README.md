# pullandpush
import subprocess
import sys

def git_pull():
    try:
        subprocess.check_call(["git", "pull"])
        print("Successfully pulled the latest changes.")
    except subprocess.CalledProcessError as e:
        print(f"Error during git pull: {e}")
    
def git_push():
    try:
        subprocess.check_call(["git", "push"])
        print("Successfully pushed changes.")
    except subprocess.CalledProcessError as e:
        print(f"Error during git push: {e}")

# Ensure Git is installed and repository is initialized
def check_git_installed():
    try:
        subprocess.check_call(["git", "--version"])
        print("Git is installed.")
    except subprocess.CalledProcessError:
        print("Git is not installed. Please install Git first.")
        sys.exit(1)

if __name__ == "__main__":
    check_git_installed()
    
    action = input("Enter 'pull' to pull changes or 'push' to push changes: ").strip().lower()
    
    if action == "pull":
        git_pull()
    elif action == "push":
        git_push()
    else:
        print("Invalid action. Please choose 'pull' or 'push'.")
