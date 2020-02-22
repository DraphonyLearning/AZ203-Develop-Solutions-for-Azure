# Function App

In this lab, we will create an image processing pipeline, which consists of the following steps:
1. A user sends a image via HTTP POST 
2. This will generate a new message in the Azure Storage Queue. The image itself is saved as Blob in the Azure Storage Blob.
3. A another Azure Function (time-triggered) runs every 15 seconds to process the image including:
    * Send image to Cognitive Service to
      * Create tags
      * Create image description 
      * Categorize
      * Detect objects, brands, faces
      * Analyze image color scheme
    * Save the result in Azure Cosmos DB
    * Crop and Resize the image to 1080p, 720p and 480i.
    * Apply some filter to your image (e.g. gray-sale, higher saturation, etc.)
    * Save the result in Azure Storage Account.
    * Don't forget the remove the message from the Queue.
4. User will be notified when Image processing is completed.

## Project setup
Each component should report its status:
  - Execusion started
  - Message sent
  - Operation Started (Resizing, Tagging, etc),
  - Operation Completed
  - Result written
  - And so on.

You can use:
  - Log Analytics Workspace
  - Storage Account Append Log (use valid JSON)
  - Application Insight

### Frontend
* Create a basic web front end for applciation, which allows the user to upload an image.

### Backend
* The backend component creates for each upload 1 message in the following queues:
    * Resizing workload queue
    * Tagging workload queue
    * Description workload queue
    * and so on

### Azure Workload
1. Create multiple time-triggered **AND** http-triggered Azure Function.
    * Is it possible to define multiple triggers?
2. Each of them should handle a seperate workload queue. 
    * For resizing the images, you can use the `SixLabors.ImageSharp` package.
    * Consider using Cognitive Service.
3. Store the result of any image processing operation.
4. Append the result of each operation to Cosmos DB:
    * You can choose which API, you would like to use.

Bonus:
    * Draw the face landmarks into image and save the result into an Blob & append it to Cosmos DB

### 