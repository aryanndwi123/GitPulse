# GitPulse

A command-line tool to visualize your Git commit history from local repositories, similar to GitHub's contribution graph.

## Overview

GitPulse scans your local Git repositories and creates a visual representation of your commit activity in the terminal. It displays a heatmap similar to GitHub's contribution graph, showing your commit frequency over the last six months.

<img width="839" alt="Screenshot 2025-03-16 at 6 53 45 PM" src="https://github.com/user-attachments/assets/33bf43d5-2b8b-4a21-9acd-39fa3ec7d9b6" />



## Features

- Scan local directories to find Git repositories
- Track commits across multiple repositories
- Filter commits by author email
- Visualize commit frequency with a colored heatmap
- Display commit activity for the last six months

## Installation

### Prerequisites

- Go 1.13 or higher
- Git installed on your system

### Installing with Go

The easiest way to install GitPulse is directly through Go:

```bash
# Download and install the binary
go install github.com/aryanndwi123/gitpulse

# Make sure your Go bin directory is in your PATH
# Add this to your ~/.bashrc, ~/.zshrc, or similar shell configuration file
export PATH=$PATH:$(go env GOPATH)/bin

# Reload your shell configuration
source ~/.bashrc  # or source ~/.zshrc if using zsh
```

After installation, you can run GitPulse from anywhere using the `gitpulse` command.

### Building from source

If you prefer to build from source:

```bash
# Clone the repository
git clone https://github.com/aryanndwi123/gitpulse.git
cd gitpulse

# Build the application
go build -o gitpulse .

# Optionally, move the binary to a directory in your PATH
sudo mv gitpulse /usr/local/bin/
```

## Usage

### Adding repositories

First, add directories containing Git repositories to track:

```bash
gitpulse --add /path/to/your/projects
```

You can add multiple directories by running the command multiple times.

### Viewing stats

To view your commit stats, run:

```bash
gitpulse --email your.email@example.com
```

Replace `your.email@example.com` with the email you use for Git commits.

## Understanding the Visualization

The visualization is a heatmap with:

- Days of the week on the left (Mon, Wed, Fri)
- Months across the top
- Colored cells representing commit counts:
  - Grey (`-`): No commits
  - White: 1-4 commits
  - Yellow: 5-9 commits
  - Green: 10+ commits
  - Purple: Today's cell (regardless of count)

## Configuration

The application stores repository paths in `~/.gogitlocalstats`. This is a simple text file with one repository path per line. You can manually edit this file if needed.

## Development

### Project Structure

- `main.go`: Entry point with command-line parsing
- `scan.go`: Functions for finding and storing Git repository paths
- `stats.go`: Functions for retrieving and visualizing commit data

### Dependencies

- `gopkg.in/src-d/go-git.v4`: Go Git implementation for retrieving commit history


## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Inspired by GitHub's contribution graph
- Thanks to the go-git library for Git functionality
- Special mention to [Flavio Copes](https://github.com/flaviocopes)
