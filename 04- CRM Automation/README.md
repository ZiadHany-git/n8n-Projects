# CRM (Customer Relationship Management) Automation

- This workflow makes it really easy for you as a recruiter, someone working in the HR department, or anyone who is looking for the right people to hire.

## The idea behind it

- The applicant fills out a form, then their information is sent to an admin or whoever is responsible.
- Then it's all up to you to send the message containing either **"Congratulations! You are accepted."** or **"Unfortunately, you are declined."**
- You just click a button on Telegram. You can review the person's information to decide whether you want to accept them or not. I think it's a very good idea because you have full control while putting in the least amount of effort (you just trigger the workflow to be executed).

### How it was done

- First, we start with an **On Form Submission** node to let the applicant fill out a form with all the information that we need.
- Then we append this information into a spreadsheet using **Google Sheets**.
- After that, we send a notification to the admin or the responsible person in this process. The message contains the essential information required to decide whether the applicant is suitable for the job or whatever they are applying for.
- Next (in **Workflow 2**), after the admin clicks either the **[Yes]** or **[No]** button, the `callback_data` is passed into a **Switch** node. If the admin clicks **[Yes]**, a message saying **"You are accepted."** is sent to the applicant. If the admin clicks **[No]**, a message saying **"You are declined."** is sent to the applicant. All of that is handled by the **Switch** node.
- Of course, there are two **Gmail** nodes because there are two possible cases in the **Switch** node.

> [!NOTE]
> I created two workflows because I can't publish a workflow with two triggers at the same time. So, I separated the project into two workflows and published both of them.
>
> Some data has been removed from `workflow1.json` and `workflow2.json`.
>
> You can use this idea and improve it to build incredible automations in just a few minutes using different applications, not just Telegram.
>
> I used **ngrok** to create a tunnel that connects Telegram with my n8n instance because I am currently running n8n locally on my device (localhost).
