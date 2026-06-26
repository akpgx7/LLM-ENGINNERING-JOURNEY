# Brochure Generator (Local LLM via Ollama)

Generates a Brochure from a company webpage's content using **Gemma3** running locally via
**Ollama** — no paid API required.

## How it works
1. Scrapes the target website's text content (`scraper.py`)
2. Sends it to a locally running Gemma3 model through Ollama's
   OpenAI-compatible API
3. Returns a clean Brochure as intended with a typewriter like animation

## Setup
\`\`\`bash
# 1. Install Ollama: https://ollama.com
# 2. Pull the model
ollama pull gemma3

# 3. Install Python deps
pip install -r requirements.txt

# 4. Run
brochure.ipynb
\`\`\`

## Example output
>Found 7 relevant links
>## Coursera: Unlock Your Potential – Globally
>
>**A Brochure for Customers, Investors & Recruits**
>
>**(Image: A diverse group of people collaborating on a digital screen, overlaid with the Coursera logo)**
>
>**Coursera is revolutionizing education by providing access to world-class learning experiences for anyone, anywhere.** Founded in 2012 by Andrew Ng and Daphne Koller, we’re driven by a powerful vision – that learning should be a right, not a privilege.  We partner with over 375 leading >universities and companies globally to deliver flexible, affordable, and job-relevant education through courses, Specializations, Professional >Certificates, and degree programs.
>
>**For Individuals: Invest in Yourself**
>
>*   **Learn from the Best:** Access thousands of courses taught by renowned professors and industry experts from institutions like Google, IBM, >Microsoft, Stanford University, and more.
>*   **Expand Your Skills:** Explore offerings across a wide range of fields including Data Science, Artificial Intelligence, Business, Software >Engineering, IT, Sales & Marketing, and Personal Development. 
>*   **Career Momentum:**  Gain practical skills with our trending courses like Python or Data Analytics - designed to boost your career prospects.
>*   **Affordable Learning:** Start with a free trial and save up to 40% on annual subscriptions – that’s just ₹625 per month! (Prices may vary by >region)
>
>
>
>**For Businesses: Empower Your Team**
>
>*   **Upskill & Reskill:** Equip your workforce with the latest skills in high-demand areas like AI, Data Science and more.
>*    **Save on Training Costs:**  Reduce training costs by up to 40% while simultaneously boosting team performance.
>*   **Custom Solutions**: Coursera for Business provides access to a dedicated catalog of learning content tailored to your organization's needs and goals. Explore Google Career Collection programs for entry-level training
>
>**For Universities & Governments: Transform Education**
>
>*   **Expand Reach:**  Deliver your curriculum globally, reaching millions of learners through our robust online platform.
>*   **Collaborative Innovation:** Partner with Coursera to leverage our technology and expertise in creating cutting-edge learning experiences.
>
>
>**Company Culture - Our DNA:**
>
>Coursera is built on a culture of innovation, collaboration, and impact. We're driven by the belief that education can change the world – we’ve >fostered an environment where curiosity thrives and teams work together to tackle ambitious challenges. We value diversity, inclusion, and >continuous learning! 
>
>
>
>**Careers at Coursera: Join Our Mission**
>
>We are seeking passionate individuals ready to shape the future of learning.  Coursera & Udemy have combined to create a massive powerhouse, >focused on building skills for the AI era. 
>
>*   **Opportunities:** Explore career paths in Product Development, Engineering, Marketing, Content Design and more.
>*   **Impact:** Contribute to our mission of democratizing access to education and empowering millions worldwide. 
>
>
>**Join the Coursera Community Today!**
>
>[Link to Coursera Website: www.coursera.org]
>[Social Media Links - LinkedIn, Twitter/X, Facebook] 
>**(Small Logo of Coursera)** – *Learn Without Limits.*>
>**(Small Logo of Coursera)** – *Learn Without Limits.*