# Virtual Environment Setup Instructions

## Environment Location
Full system path to the virtual environment:
```
C:\Users\[User]\Downloads\repo safety folder\environments\virtual
```

## Activation Instructions
### For Windows Command Prompt (cmd.exe)
```cmd
"C:\Users\[User]\Downloads\repo safety folder\environments\virtual\Scripts\activate.bat"
```
### For Git Bash
```bash
source "C:/Users/[User]/Downloads/repo safety folder/environments/virtual/Scripts/activate"
```

## Using with Jupyter Notebooks in VS Code
1. First install these packages in the virtual environment:
```bash
# Activate the environment first, then run:
pip install ipykernel jupyter
```

2. In VS Code:
   - Close VS Code completely if it's open
   - Reopen VS Code
   - Open your .ipynb file
   - Click on the "Select Kernel" button in the top-right corner
   - Choose "Python Environments..."
   - Select the kernel with path: `C:\Users\[User]\Downloads\repo safety folder\environments\virtual\Scripts\python.exe`

If you still don't see the kernel:
1. Make sure VS Code is completely closed and reopened
2. Try running these commands in the terminal:
   ```bash
   source "C:/Users/[User]/Downloads/repo safety folder/environments/virtual/Scripts/activate"
   python -m ipykernel install --user --name=virtual --display-name "Python (virtual)"
   ```
3. Check available kernels with:
   ```bash
   jupyter kernelspec list
   ```

## Notes
- The virtual environment must be activated every time you open a new terminal window
- You can verify the environment is activated when you see "(virtual)" at the start of your command prompt
- If VS Code asks to install Python extensions, allow it as this helps with Jupyter notebook support