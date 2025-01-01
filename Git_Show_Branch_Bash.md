

# Function to fetch the current Git branch if in a Git repository
git_branch() {
    # Check if the current directory is in a Git repository
    git rev-parse --git-dir > /dev/null 2>&1
    # If it is, append the Git branch name to the prompt
    if [ $? -eq 0 ]; then
        echo " ($(git branch 2>/dev/null| sed -n '/^\*/s/^\* //p'))"
    fi
}

# Customize the bash prompt
export PS1="\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$(git_branch)\$ "
