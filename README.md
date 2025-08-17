# claude-code-security-recommendations

**Recommendations (written by [Rami Hersonsky](https://www.linkedin.com/in/rami-hersonsky/), used Claude for assistance)**

1. Check dangerous patterns:
1. Before every Read
2. Before every edit / write
3. Before every system execution (in bash and code)
2. A. Don’t give access to git, but ask to make sh file that runs safe limited git commands only that user runs manually afterward with a key to specific git repo only

B. Backup git repo (ex: automatically) before every git repo run and at nightly
C. Work on separate git repo or at least branch every session

3. A. Work inside protected container that is mapped to single folder and have rules for firewall that can access limited whitelisted websites **(DEVELOPMENT \+ TESTING \+ PRODUCTION)**
   B. Disable curl POST and similar access (for code leakage protection if needed)
4. Run tests before commit
5. Run security check agent you trust before commit (a separate agent that there is no access to it from dev container), check:
   A. Best practices security per language
   B. backdoors (internet, passwords, etx.)
   C. date bombs
   D. Supply chain poisoning
   E. Malicious comments (eg: \#dangerous code, to refactor later on and enable
   F. Semantic equivalent meaning with different commands

6. A. Log all system commands, web search, mcp commands and external access commands that claude do and validate them for security before commit
   B. Log all suspicious file changes in prohibited places with inotify tool, and validate them for security before commit
7. Deny Read / Write / Edit / run bash commands on sensitive folders that contains sensitive data
1. Deny read to: keys / passwords, git (/version control) info, .gitignore, claude hooks, hidden files and hidden folders unless instructed directly (or in less restricted mode), files and folders that are not in working folder or its subfolders
2. Deny write to: all denied read folders & files, files and folders that are not in working folder or its subfolders

     8\. Zero-trust execution model (monitor all suspicious activities in runtime, eg: with falco)
     9\. Store kays & passwords separately from dev agent & security test agent
     10\. Run always in containers, including: development agent, security test agent, test agent, execution
     11\. Only Human approves commits, run push and runs the production system


In addition to this file, please look at:
[LICESNE] and [DISCLAIMER.md]

[Reference of the chat with Claude that helped me to create above instructions](https://claude.ai/share/7933457a-3425-48b6-b577-01f862451cc5)

