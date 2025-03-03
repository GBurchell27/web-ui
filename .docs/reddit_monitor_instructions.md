# Reddit Monitoring System for Systematic Reviews: Detailed Instructions

## System Setup and Configuration

1. Open your web browser application.
2. Navigate to the Reddit website by entering "https://www.reddit.com" in the address bar.
3. Log in to your Reddit account by:
   - Clicking the "Log In" button in the top-right corner.
   - Entering your username and password in the respective fields.
   - Clicking the "Log In" button to authenticate.

4. Navigate to the specific subreddit of interest by:
   - Clicking in the search bar at the top of the page.
   - Typing "r/" followed by the subreddit name.
   - Pressing Enter or clicking on the subreddit in the dropdown results.

## Monitoring Configuration

5. Set up a monitoring system to scan new posts in the subreddit by:
   - Creating a connection to the Reddit API using your application credentials.
   - Setting the monitoring frequency to check for new posts every 15 minutes.
   - Configuring the monitoring system to run continuously in the background.

6. Configure keyword detection parameters:
   - Add the following keywords to the monitoring system:
     * "systematic literature review"
     * "systematic review"
     * "meta-analyses"
   - Set the system to perform case-insensitive matching.
   - Configure the system to check both post titles and post content for these keywords.

## Post Processing Workflow

7. When a new post containing any of the target keywords is detected:
   - Extract the following data from the post:
     * Post title
     * Post content/body
     * Post URL
     * Author username
     * Timestamp
     * Subreddit name

8. Prepare the extracted data for storage by:
   - Formatting the data as a JSON object.
   - Generating a unique identifier for the post.
   - Adding metadata tags for the detected keywords.

## Vector Database Operations

9. Connect to your company's vector database by:
   - Opening the database connection using the appropriate credentials.
   - Verifying the connection is active and authenticated.

10. Store the post information in the vector database by:
    - Converting the post text into a vector embedding.
    - Storing the embedding along with the original post data.
    - Tagging the entry with relevant metadata (keywords, timestamp, source).

11. Perform a similarity search in the vector database to:
    - Find company information relevant to the post content.
    - Retrieve the top 5 most similar documents from your company's knowledge base.
    - Extract the content, URLs, and metadata from these relevant documents.

## Response Generation

12. Prepare data for the language model by:
    - Combining the original Reddit post content with the retrieved company information.
    - Formatting this combined data according to the language model's input requirements.
    - Adding appropriate context and instructions for the language model.

13. Send the prepared data to the large language model by:
    - Opening a connection to the language model API.
    - Submitting the data package to the model.
    - Setting appropriate parameters for response length, creativity, and formatting.

14. Configure the language model prompt to:
    - Generate a helpful and informative response to the original post.
    - Include relevant information from the company's knowledge base.
    - Naturally incorporate references to relevant company products or services.
    - Maintain a helpful, non-promotional tone.
    - Format the response appropriately for Reddit.

## Response Posting

15. Post the generated response to the original Reddit thread by:
    - Navigating to the original post URL.
    - Clicking on the "Comment" or "Reply" button.
    - Pasting the generated response into the comment field.
    - Reviewing the response for formatting and appropriateness.
    - Clicking the "Submit" or "Post" button to publish the comment.

16. Record the interaction in your system by:
    - Logging the original post ID, the response content, and timestamp.
    - Updating the vector database entry with information about the response.
    - Flagging the post as "responded" in your monitoring system.

## Continuous Operation

17. Return to step 5 to continue monitoring for new posts.
18. Implement a periodic review process to:
    - Check the performance of responses every 7 days.
    - Update keywords or search parameters based on performance.
    - Refine the language model prompting based on engagement metrics.

## Error Handling

19. If connection to Reddit fails:
    - Log the error details.
    - Wait 5 minutes and attempt to reconnect.
    - Send notification to system administrator if connection fails 3 consecutive times.

20. If vector database operations fail:
    - Log the error and the post data locally.
    - Attempt to retry the database operation up to 3 times.
    - Queue failed operations for later processing if retries are unsuccessful.

21. If language model generation fails:
    - Log the error and input data.
    - Attempt with modified parameters up to 2 times.
    - Flag the post for human review if automated response generation is not possible. 