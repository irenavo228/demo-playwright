# 1. (Optional) Activate your venv
python -m venv .venv
source .venv/bin/activate        # macOS/Linux
.\.venv\Scripts\activate         # Windows PowerShell

# 2. Install libs
python -m pip install --upgrade pip setuptools wheel
pip install -r requirements.txt
playwright install chromium firefox
npm install -g allure-commandline

# 3. Run test
pytest --browser=chromium --env=local --mode=headed tests/test_login.py -v
python gen_report.py

# 4. Build image on Docker:
docker buildx build -t demo-playwright:latest ../demo-playwright