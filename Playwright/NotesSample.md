> [!NOTE]
> Here is a sample of notes I take in my learning process

# Setting up a basic project with Playwright
## Playwright, VS Code, Python, KDE NEON - setting a basic project in a virtual environment
1. Open project in VS Code
2. Open a bash console in VS Code
3. Creating a virtual environment in the folder module_1 or using another name
    ```console
    python3 -m venv module_1
    ```
4. Activate the virtual environment
    ```console
    source module_1/bin/activate
    ```
5. Install pytest while being in a virtual environment
    ```console
    pip install pytest-playwright
    ```
6. Install playwright dependency - browser
   
> [!NOTE]
> ``` console
> playwright install
> ```
> Did not work in the terminal, an error occurred 
> <img width="898" height="128" alt="image" src="https://github.com/user-attachments/assets/528156e8-c1ea-49b6-8db5-b65f2d71fd35" />

> [!TIP]
> workaround, but a bad practice, it allows having Python and NodeJS files:
> Press F1 and type `Playwright install` - will work when the extension `Playwright for VS Code` is installed
> It will generate in the console the following line
> ```console
> npm init playwright@latest --yes "--" . '--quiet' '--browser=chromium' '--browser=firefox' '--browser=webkit' '--gha' '--install-deps'
> ```

> [!NOTE]
> Alternative workaround is to build a container with an Ubuntu image - test out in free time

> [!WARNING]
> It will log out of the virtual environment and install to the current selected folder, use the command to generate a console command, use a dummy folder to generate a console line and then use it in the virtual environment

7. If everything is correct, at the end line, "Happy Hacking!" should appear

<img width="798" height="632" alt="image" src="https://github.com/user-attachments/assets/ad96b276-dcd5-4706-b20d-e5216e9faaee" />

8. Create basic test_example.py in

```python
import re
from playwright.sync_api import Page, expect

def test_has_title(page: Page):
    page.goto("https://playwright.dev/")

    # Expect a title "to contain" a substring.
    expect(page).to_have_title(re.compile("Playwright"))

def test_get_started_link(page: Page):
    page.goto("https://playwright.dev/")

    # Click the get started link.
    page.get_by_role("link", name="Get started").click()

    # Expects page to have a heading with the name of Installation.
    expect(page.get_by_role("heading", name="Installation")).to_be_visible()
```
9. Running pytest should now work

<img width="798" height="632" alt="image" src="https://github.com/user-attachments/assets/836d6fa6-03f9-4565-af03-02bab923d4a5" />
<img width="1095" height="654" alt="image" src="https://github.com/user-attachments/assets/0008e19f-9293-4b24-9c9b-383910ac281f" />

> [!NOTE]
>  pytest takes iteams = files from the `tests` folder
    
## Setting REPL using console only - quick check command
1. Open the console in the folder of the existing project, for example, as from the first instruction
2. Run the console from the folder of the project 
## Recording steps
> [!NOTE]
> - There is a possibility to turn the manual click into generated code that can be saved.
> - It has to be run in the folder before `tests`
```console
playwright codegen https://demo-bank.vercel.app/
```
> [!NOTE]
> - after running the record window select in the window programming language before clicking to generate the code in the specific language
> - default is nodejs
> - runs only with `test_***` in name 
for Node.js
```console
npx playwright test
```
or for Python
```console
pytest
```
