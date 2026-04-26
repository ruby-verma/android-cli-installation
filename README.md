# android-cli-installation
Guide to install andtoid cli when existing sdk manager

### Step 1: Download the Binary Directly
https://dl.google.com/android/cli/latest/windows_x86_64/android.exe

### Step 2: Place it in your SDK Path
To ensure the new "Agent" tool works with your existing SDK, move the downloaded ``android.exe`` into your ``bin`` folder:
1.	Navigate to: ``~\Android\Sdk\cmdline-tools\latest\bin``
2.	Paste the ``android.exe`` file into this folder.
   
>Note: You should now see sdkmanager.bat, avdmanager.bat, and android.exe all in the same folder.)_
>

### Step 3: Verify the "Agent" Command
Open a new PowerShell window and type:
```Bash
android –version
```
If you see a version number (like ``1.0.0``), you have successfully bypassed the installation wall.

### Step 4: Initialize for Agents (``android init``)
Now you can proceed with the Agentic workflow. Navigate to your project folder (e.g., your Android App source code) and run:
	``android init``
This command will:
- Create a ``.androidrc`` (or similar) configuration.
- Prepare your project to be "read" by AI agents.
- Install the base ``android-cli`` skill.

### Step 5: Adding Skills (The Agentic "Brain")
To add specific capabilities like the Room Database logic or UI Migration skills you were looking for:
```Bash
	android skills add –all
```

- Why use ``--all?`` Since your network is having certificate issues, it's better to pull all standard skills at once rather than one by one later.
- ``Skill.md``: After running this, look for new .md files in your project. You can manually append your Room Database schema to these files to "ground" the AI in your specific data structure.
***
Now the Setup is complete, let create new project
### 1.	Basic Project Creation
To create a project with the default settings (which uses the Empty Activity template with Jetpack Compose and AGP 9.x), run:
```Bash
android create --name="MyAgenticApp" --output=”<PAHT_OF_THE_PROJECT_FOLDER>”
```

### 2.	Choosing a Template
If you want something other than the default "Empty Activity," you can see the list of available templates by running:
```Bash
android create –help
```
Common templates usually include:
- ``empty-activity-agp-9`` (The default)
- ``compose-room-agp-9`` (Useful since you are interested in Room schemas)
- ``view-bridge-agp-9`` (For XML to Compose migration setups)

### 3. Creating a Project with a Specific Template
If you want to start with a project that already has Room Database and Jetpack Compose configured, use:
```Bash
android create --output="./MyRoomProject" compose-room-agp-9
```

### 4. Advanced Flags
- ``--dry-run``: This is incredibly useful for testing. It will simulate the creation process and show you exactly which files and folders would be created without actually writing anything to your disk.
```Bash
android create --name="TestApp" --output="./test" --dry-run
```
- ``--verbose``: Use this if you want to see the detailed logs of every file being copied from the internal template into your directory.

### 5. Why this matters for your workflow
Since you are setting this up for agentic AI, the ``android create`` command does more than just make files. It prepares the project for the ``android init`` command you used earlier.

Once the project is created, you can immediately follow up with:

1. ``cd MyAgenticApp``
2. ``android init`` (to set up the AI context)
3. ``android skills add --all`` (to give your AI agent the tools it needs)

### References
https://developer.android.com/tools/agents/android-cli


