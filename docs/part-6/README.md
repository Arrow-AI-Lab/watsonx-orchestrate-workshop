# Creating the Skillflow

In this section, you’ll create the Skillflow that will be used as a Skill-based action in your AskSales AI assistant.

## 1. Navigate to Skill Studio

From the watsonx Orchestrate hompage click **Skill Studio**

![create action 1](./images/wxo-01-2025-03-08.png)

## 2. Create new skillflow

Click on Create dropdown and then select **Skill flow** (1)

![create action 2](./images/wxo-02-2025-03-08.png) 

Click on the Pencil icon (1) and name (2) your skillflow **Send Email to Salesforce Contact**.
![create action 2](./images/wxo-02-1-2025-03-08.png) 

## 3. Add Skills to the Skillflow

Add skill to the skillflow by clicking on the + icon (1) between Start and End.
On the side panel that appears, search for **Salesforce for askSales** on the search bar (2), then find and **click** the Salesforce for AskSales (3).

![create action 3](./images/wxo-03-2025-03-08.png)

You will see two skills from **Salesforce for askSales**.

Add **Salesforce Customer List** skill to the flow by clicking on Add Skill (4).
![create action 4](./images/wxo-03-1-2025-03-08.png)

Complete the same steps to add five more skills to the flow.

- From "Salesforce for askSales" add Get customer contacts by ID

- From "Custom forms" add Input form

- From "AskSalesSkils" add generateSalesEmail

- From "AskSalesSkill" add generateEmailTitle

- From "Microsoft Outlook" add Send an email 

When finished, your skill flow should look similar to the image below:

![create action 5](./images/wxo-03-2-2025-03-08.png)

You must now start mapping the inputs and outputs of the skills in the flow. First, click on the **Get customer contacts by ID** skill 

![create action 14](./images/wxo-14-2025-03-08.png)

On the side panel that opens up, click on the customer_id field, then click on the Salesforce Customer List option

![create action 15](./images/wxo-15-2025-03-08.png)

Click the id input option, then enable the Hide this form from the user toggle

![create action 16](./images/wxo-16-2025-03-08.png)

Now click on the Input form between the Get customer contacts by ID and the generateSalesEmail skills

![create action 17](./images/wxo-17-2025-03-08.png)

Click on Add input field on the panel that opens to the right. Then choose on the Paragraph text option and click Next

![create action 18](./images/wxo-18-2025-03-08.png)

In the Display label field, write this: “Give me instructions on how to generate the email”. We are using this 
to make the prompt that shows up to the user for the GenAI skill to be more conversational, and have a 
larger input field (paragraph input as opposed to simple text input). When you’re done, click Apply.

![create action 19](./images/wxo-19-2025-03-08.png)

Now click on the generateSalesEmail skill to configure its inputs

![create action 20](./images/wxo-20-2025-03-08.png)

You’ll see all the variables you made when creating this skill as inputs here. Most of them will 
used to enhance the prompt sent to the GenAI, as we saw earlier. There are several ways to populate 
these variables dynamically, but for this demo, we’ll hard code values in most of them, only leaving 
the emailGenerationPrompt be mapped to dynamic inputs. Let’s do this step-by-step.

![create action 21](./images/wxo-21-2025-03-08.png)

Hover the mouse over the Role field and a pencil icon will show up to its right. Click on this icon to specify
a default value for this variable

![create action 22](./images/wxo-22-2025-03-08.png)

Write Sales Specialist as the default value for the Role field

![create action 23](./images/wxo-23-2025-03-08.png)

For the userName and userEmail fields, you can insert your own name and email or create a 
name and email for the demo’s persona. As mentioned previously, these pieces of information could 
be acquired dynamically through several ways, and the intention here is to simulate watsonx 
Orchestrate getting this data from the profile of the user that is logged in. Since the focus of this 
demo is to demonstrate AI-guided actions and custom GenAI skills, let’s continue with hardcoded 
information to proceed faster.

![create action 24](./images/wxo-24-2025-03-08.png)

Now, click on the customerName field to map its input

![create action 25](./images/wxo-25-2025-03-08.png)

Map the Name output of the Get customer contacts by ID skill to the customerName field

![create action 26](./images/wxo-26-2025-03-08.png)

Now click on the emailGenerationPrompt field to map its input

![create action 27](./images/wxo-27-2025-03-08.png)

Map the Give me instructions on how to generate the email output of the Input form to the emailGenerationPrompt field

![create action 28](./images/wxo-28-2025-03-08.png)

To finish setting up the generateSalesEmail skill, enable the Hide this form from the user toggle

![create action 29](./images/wxo-29-2025-03-08.png)

Now, click on the GenerateEmailTitle skill

![create action 30](./images/wxo-30-2025-03-08.png)

Map the generated_text output of the generateSalesEmail skill to the emailBody field
![create action 31](./images/wxo-31-2025-03-08.png)

Enable the Hide this form from the user toggle on the generateEmailTitle skill

![create action 32](./images/wxo-32-2025-03-08.png)

Finally, let’s setup the Send an email skill

![create action 33](./images/wxo-33-2025-03-08.png)

Click on the body.Content field

![create action 34](./images/wxo-34-2025-03-08.png)

Click on the generateSalesEmail option, then click generated_text

![create action 35](./images/wxo-35-2025-03-08.png)

Now click on the Subject field

![create action 36](./images/wxo-36-2025-03-08.png)

Map the generated_text output of the generateEmailTitle skill to the Subject field. 
Be careful not to confuse it with the generated_text output from the generateSalesEmail skill!

![create action 37](./images/wxo-37-2025-03-08.png)

Now click on the To field

![create action 38](./images/wxo-38-2025-03-08.png)

Click on the Get customer contacts by ID option, then click Email

![create action 39](./images/wxo-39-2025-03-08.png)

Next, to finish creating your skill flow, click on Actions to the top right

![create action 40](./images/wxo-40-2025-03-08.png)

Click Enhance

![create action 41](./images/wxo-41-2025-03-08.png)

On the message box that pops up, click Save and close

![create action 42](./images/wxo-42-2025-03-08.png)

On the enhancement screen, click Publish to the bottom right

![create action 43](./images/wxo-43-2025-03-08.png)

You should now see the Send Email to Salesforce Contact skill flow among the published skills in your tenant.

![create action 44](./images/wxo-44-2025-03-08.png)

