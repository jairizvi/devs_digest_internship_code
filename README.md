This is my intern project at ___________, a startup pertaining to AI-powered college counseling. The goal of my project was to create a tool that users of the AI college counselor website can engage with and ask questions. In the end, I had created a tool where users can ask any question pertaining to college, and then the users would get an AI-generated response based off of real student and parent experiences scraped from the web, texts that were carefully selected to match the specific topic of the user's question. Here is the more technical side of my project:

My code works in 4 steps.

**Step One: The Scraping**
This step consists of scraping all of the threads from all of the 552 categories on the College Confidential site (a Reddit/Quora for college). The College Confidential website is a place where students and parents can discuss topics surrounding college. I scraped all 440,000 threads, getting the first post and a bunch of other metadata from the website. I would use a proxy rotator and rate throttling so I would not get rate limited from the website I was scraping from. I only scraped the pages 0-100 for each category.

**Step Two: The Embeddings** After I got the first post of each thread on the College Confidential website, and assigned something called an “embedding” to each of the first posts. “Embeddings are vectors that represent real-world objects, like words, images, or videos, in a form that machine learning models can easily process.” - Cloudflare. In my specific case, an embedding was an array of 8-bit floats (numbers) that consisted of 1536 items, representing the text scraped for each first post in the threads.

**Step Three: The Similarity Search**
The computer could now interpret the content for each thread based off of the embeddings, and perform a “similarity search” where you can use a query to ask any question of your own about college. The computer would then be able to find the most similar posts, assigning a similarity score to each post.

**Step Four: The GPT Response**
After I got the three most similar threads to a given question, I would get the first 10 responses to each first post for each thread, scraping it from the thread URL provided in the metadata. I gave the Chat GPT 3.5 Turbo API a prompt providing the given question, and then giving the text from the responses as context. I would say something along the lines of “Here is my question: _______________. Answer the question based on this information: __________.” It would then return a useful response powered by a real person's response to a similar question on the College Confidential website.



