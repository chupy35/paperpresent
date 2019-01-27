---?color=black
### Studying Trends and characteristics in the Tensorflow Models
&nbsp;
@box[bg-green text-white demo-box-text-padding rounded](Workload-Aware Monitoring of a 1&1 E-mail System)

---?color=black
#### @color[white](**Predicting Performance Quality in Distributed Systems**)

![](template/img/palladioperf.png)

---?color=black
@title[Goals and Questions]

@snap[north-west text-white]
Goals and Questions
@snapend

@snap[south-west list-content-concise span-100 text-white ]
@ol
- How to integrate model-based predictions into the run-time monitoring of systems?
- How to model a large and distributed system consisting of several hundred servers?
- How to calibrate the prediction model only on the basis of existing run-time monitoring data without running experiments? 
@olend
<br><br>
@snapend

---?image=template/img/bg/black.jpg&position=right&size=50% 100%
@title[Text + Image]

@snap[east span-50 text-white text-05]
@ul[split-screen-list text-09 span-90](false)
**System Description**

&nbsp;

- One of the biggest hosters and leading domain registrars
- Backend: E-mail sending, receiving requests, persistence via restful HTTP services, POP3, or IMAP
- Service oriented paradigm
- Individual deployment per component on dedicated servers in redundant instances.
@ulend
@snapend

@snap[west]
@img[split-screen-img span-50](template/img/img1.png)
@snapend

---?image=template/img/bg/black.jpg&position=right&size=50% 100%
@title[Text + Image]

@snap[east span-50 text-white text-05]
@ul[split-screen-list text-09 span-90](false)
- STORE: folder structures of mailboxes and attachments are saved
- SERIE and DBFM db: fast access to internal instances informations which single mailboxes are dedicated
- Mail Delivery Agents (MDAs) and mail transfer agents (MTAs): located on mail exchanger (MX) and mail proxy (MP) servers)
- External clients connect to the proxy with IMAP and POP3 requests and forward requests to the STORE servers
- Clients use Restful api
- More components added like antivirus and other tasks
@ulend
@snapend

@snap[west]
@img[split-screen-img span-50](template/img/img1.png)

---?image=template/img/bg/orange.jpg&position=right&size=50% 100%
@title[Heading + List Body]

@snap[west text-16 text-bold text-italic text-orange span-50]
Modeling
@snapend

@snap[west]
@img[split-screen-img span-50](template/img/img2.png)

@snap[east text-white span-45]
@ol[split-screen-list text-06](false)
**Modeling - Workload-aware Performance Montoring**

&nbsp;

- Main activities: Model preparation, Model calibration and prediction and comparison 
- Model has to be specified only once
- 1st activity: Model describing the system 
- 2nd activity: Available hardware resources are described 
@olend
@snapend

---?color=black

@snap[west span-40]
# Analysis
@snapend

@snap[north-east span-40 fragment text-06]
@box[bg-purple text-white](.#Prediction of expected resource utilization requires measuring the current workload.)
@snapend

@snap[east span-40 fragment text-06]
@box[bg-orange text-white](.#Prediction model is completed with the specification of system's usage within the Usage Model generation.)
@snapend

@snap[south-east span-40 fragment text-06]]
@box[bg-pink text-white](.#The resulting Usage-Model is used as an input to the performance prediction, after collecting performance metrics and the prediction, they are analyzed and compared)@snapend

---?color=#8ea33a
@title[Application of the Workload-Aware Performance Monitoring Process In the following, we present the application of our approach in the industrial context]

@snap[north-west]
#### @color[white](**Store subsystem**)
@snapend

@snap[west span-50]
@ul[spaced text-white text-05]
- SGATE component handles internal requests from other components (Proxy - Store communication)
- For availability and prevent data loss Store server run as a cluster of two servers
- Each clients mailbox is associated with one server
- In case of failure the other server takes responsibility and the backup is for persistency
- Distributed Load
- SGATE, IMAP and POP3 -> 10 servers
- BACKUP -> 22 servers
@ulend
@snapend

@snap[east span-45]
@img[shadow](template/img/img3.png)
@snapend

---?image=template/img/bg/green.jpg&position=left&size=50% 100%
@title[Performance Modeling Study]

@snap[north-west span-50]
###### @color[white](**Performance Modeling Study**)
@snapend

@snap[west span-45]
@ul[spaced text-white text-05]
**Model Preparation:**
- API of SGAE supports multiple requests
- Log files analyzed and interviews with architects and developers
- Request is relevant its its occurrences within the workload is higher than 1%
@ulend
@snapend

@snap[east fragment]
@img[split-screen-img span-50](template/img/img4.png)
@snapend

---?image=template/img/bg/green.jpg&position=left&size=50% 100%
@title[Performance Modeling Study]

@snap[north-west span-50]
@snapend
@snap[west span-40 text-11 text-white]
Description and Modeling of different components in the Palladio Repository Model
@snapend

@snap[east fragment]
@img[split-screen-img span-50](template/img/img5.png)
@snapend

---?image=template/img/img6.png&position=center&size=100% 100%

@title[Performance Modeling Study]

---?image=template/img/bg/green.jpg&position=left&size=50% 100%
@title[Performance Modeling Study]

@snap[north-west span-50]
@snapend
@snap[west span-40 text-11 text-white]
For each cluster only one node within the resource environment was modeled
@snapend

@snap[east fragment]
@img[split-screen-img span-50](template/img/img7.png)
@snapend

---?image=template/img/bg/black.jpg&position=right&size=50% 100%
@title[Model Calibration]

@snap[east span-50 text-white text-05]
@ul[split-screen-list text-09 span-90](false)
**Model Calibration**

&nbsp;

- For each server log files and monitoring data were analyzed
- In Proxy server resources are CPU and network connection.
- HDD usage is very low
- In Store servers HDD, CPU and network is heavy demanding
- Focus on Proxy Server calibration
@ulend
@snapend

@snap[west]
@img[split-screen-img span-50](template/img/img8.png)
@snapend

---?image=template/img/bg/black.jpg&position=right&size=50% 100%
@title[Model Calibration]

@snap[east span-50 text-white text-05]
@ul[split-screen-list text-09 span-90](false)
**Model Calibration**

&nbsp;

- For calculate absolute resource demands, available resources has to been considered 
- Differentiation between resource demands with fixed value per request and the ones that depend in the contained data size
- Behavioral descriptions are annotated with derived resource demands.
- Model of the balancing behavior with a ProbabilisticBranchAction 
@ulend
@snapend

@snap[west]
@img[split-screen-img span-50](template/img/img9.png)
@snapend

---?image=template/img/bg/black.jpg&position=right&size=50% 100%
@title[Model Calibration]

@snap[east span-50 text-white text-05]
@ul[split-screen-list text-09 span-90](false)
**Prediction and Comparison**

&nbsp;

- For each external interface a dedicated usage profile is defined in the Usage Model 
@snapend

@snap[west]
@img[split-screen-img span-50](template/img/img10.png)


---?image=template/img/bg/green.jpg&position=left&size=50% 100%
@title[Evaluation]

@snap[north-west span-50]
###### @color[white](**Evaluation**)
@snapend

@snap[west span-45]
@ul[spaced text-white text-05]
**Prediction and Comparison**

&nbsp;

- Automatic tools to collect, parse and analyze logs
- Values are integrated in an XML representation of the usage profiles replacing the previous inserted placeholders values
- Usage profiles used for predictions and mismatches are identified 
- Detection during a planned software update
- Validation is done by conducting benchmarks or controlled experiments and comparing with the predicted values 

@ulend
@snapend

@snap[east fragment]
@img[split-screen-img span-50](template/img/img12.png)
@snapend

---?color=black

@snap[north-west span-40 text-07]
@box[bg-green text-white demo-box-step-padding](1. #Experience gained is not limited to email systems)
@snapend

@snap[north-east span-40 text-07]
@box[bg-orange text-white demo-box-step-padding rounded](2.#Large-Scale systems provide business-critical functionality and monitoring is detailed)
@snapend 

@snap[south-east span-40 text-07]
@box[bg-pink text-white demo-box-step-padding](3. #PCM can serve as an architectural documentation and updates it)
@snapend

@snap[south-west span-40 text-07]
@box[bg-blue text-white demo-box-step-padding waved](4. #CPU Usage is more precise than HDD because of writing rate)
@snapend

@snap[midpoint]
@fa[refresh fa-3x]
@snapend

@snap[south-west template-note text-gray]
LEARNED LESSONS.
@snapend
