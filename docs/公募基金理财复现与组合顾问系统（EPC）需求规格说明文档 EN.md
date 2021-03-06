# Requirements of Mutual fund/financial management reapperence and advisory  portfolio system (EPC)

[toc]

---

## 1. Introduction

### 1.1 Purpose

The purpose of this document is to describe the functional and non-functional requirements of the mutual fund/financial management reapperence and advisory  portfolio system(EPC). The developer team's software system implementation and verification work are based on this document.

All requirements contained in this documentation have high priority unless noted.

### 1.2 Scope

The Public Fund Analysis and Recommendation System is a business system developed for bank staff and customers who have investment needs for public funds. The system aims to help staff and customers analyze the investment of public funds and provide recommended investment portfolios. The key business functions are investment history recurrence analysis and portfolio recommendation.

Through the application of the public fund analysis and recommendation system, it is expected that staff and clients will improve their ability to analyze the investment history of the subject being analyzed, thus realize a more reasonable investment portfolio and gain more profits.

## 2. General description

### 2.1 Product Outlook

#### 2.1.1 Background and opportunities

Public funds, a relatively new form of investment, have gained greater attention in today's financial markets. For banks, staff need to show customers the investment history of funds and sell them products;  for individual customers, they need a system that provides fund portfolio recommendations; while for bank branch staff, they need to analyse the details of the fund portfolio.

We noticed this and expected to assist both of these clients by developing a public fund analysis and recommendation system to achieve higher product sales and investment returns.

#### 2.1.2 Business requirements

* **BR1**: After six months of using the system, account manager users will be able to better conduct fund product sales operations, and business volume and business revenue will increase.
* **BR2**: After six months of using the system, individual investor users will be able to achieve a more than satisfactory return on their investment.
* **BR3**: When using the system at any time, analyst users will be able to easily analyze fund portfolio details.

### 2.2  System fuctions

* **SF1**: Visualization of historical investment data (wealth management or funds) uploaded by users (historical reproduction)

* **SF2**: Comparing the user's investment history with the results of the recommendation system under different risks levels (comparative recurrence).

* **SF3**: Providing users with portfolio recommendations for the current period.

* **SF4**: Providing portfolio recommendations at a certain time in the past.

* **SF5**: Providing a document with portfolio details can be viewed or downloaded

* **SF6**: Providing a customer tracing blank to customer manager for help

### 2.3 User characteristics

| User type                 |                                                              |
| ------------------------- | ------------------------------------------------------------ |
| Bank staff                | This type of user uses the system for the purpose of showing her clients the history investment profile of the client, comparing the differences between the recommended fund investment products, then trying to convince the client to buy the fund products and thus provide recommendations for the fund portfolio. |
| Ordinary individual users | The purpose of these users to use the system is to get fund portfolio recommendations based on the different risk levels they can bear, the system needs to provide high, medium and low risk levels of fund portfolio recommendations. |
| Data analysts             | These users are using the system for research purposes, are concerned about the algorithms and data behind the system, and need to be provided with a document with details about the portfolio. |

### 2.4 Constraints

* **CON1**: System interacts using a web interface.
* **CON2**:  The server side is developed using Python, while the client side using Vue framework.

### 2.5 Assumptions and dependencies

* **AE1**: All users can oprate computer proficiently.
* **AE2**: Bank staff has access to her costumers' investment history.
* **AE3**: The system only provides recommendations for fund investment, and does not force or act as an agent for the user's investment behavior

## 3. Detailed description of demands

### 3.1 External Interface Requirements

#### 3.1.1 User Interface

* **UI1**: Login screen
  * Signup screen
* **UI2**: User-type-selection screen
* **UI3**: Professional User Interface
  * Historical investment input Interface
  * historical reproduction Interface
  * portfolio recommendations Interface
  * customer tracing blank Interface
* **UI4**: Ordinary User Interface
  * portfolio recommendations Interface

* **UI5**: Data Analysis Interface

#### 3.1.2 Communication Interface

* **CI**: Client and server communicate through HTTP requests.

### 3.2 Functional Requirements

#### 3.2.1 Uploading investment history

##### 3.2.1.1 Characteristic description

User uploads the excel file of investment history to the server

##### 3.2.1.2 Stimulus/Response sequences

* Stimulus: User uploads the file of investment history
* Response: The system displays uploaded files.
* Stimulus: User uploads mismatched file formats.
* Response: The system displays a file format error and prompts to re-upload
* Stimulus: User clicks the upload button.
* Response: The system displays the upload result.

 ##### 3.2.1.3 Related functional requirements

None

-----

#### 3.2.2 History recurrence

##### 3.2.2.1 Characteristic description

The system visually displays the investment history documents uploaded by users and compares them with the CSI 300 index or financial product index.

##### 3.2.2.2 Stimulus/Response Sequence

- Stimulus: Users click to jump to the investment recurrence page
- Response: The system displays historical recurrence data as a line chart.

##### 3.2.2.3 Related functional requirements

| Functional Requirements            | Description                                               |
| ---------------------------------- | --------------------------------------------------------- |
| 3.2.1 Uploading investment history | History Recurrence shows the uploaded investment history. |

-------

#### 3.2.3 Comparative Reproduction

##### 3.2.3.1 Characteristic description

The system visually displays the investment history uploaded by the user and the profits of the recommended system's portfolio in line with the historical asset movement.

##### 3.2.3.2 Stimulus/Response sequence

- Stimulus: Users click to jump to the investment recurrence page
- Response: The system displays the return in the form of a line graph under a certain risk situation (the default risk level for fund investment users is high, for financial investment users is low).
- Stimulus: The user chooses to switch to a certain risk level
- Response: The system shows a comparison of returns for different risk scenarios

##### 3.2.3.3 Related Functional Requirements

| Functional Requirements            | Description                                                  |
| ---------------------------------- | ------------------------------------------------------------ |
| 3.2.1 Uploading investment history | Compare Recurrence needs to show the uploaded investment history records. |

----

#### 3.2.4 Portfolio Recommendations

##### 3.2.4.1 Characteristic description

The system provides users with portfolio recommendations for current time periods at different risk levels.

##### 3.2.4.2 Stimulus/Response Sequence

- Stimulus: User clicks to jump to the recommended portfolio page
- Response: The system uses a pie chart to show the portfolio recommendation for the current time period under a certain risk profile (default is high).
- Stimulus: The user chooses to switch to a certain risk level
- Response: The system displays portfolio recommendations for different risk scenarios.

##### 3.2.4.3 Related Functional Requirements

None

----

#### 3.2.5 Historical investment portfolio

##### 3.2.5.1 Characteristic description

The system provides the user with portfolio recommendations for a certain time period in history, which requires the user to select a certain time period in history

##### 3.2.5.2 Stimulus/Response Sequence

- Stimulation: The user chooses a certain time period
- Response: The system displays the selected time period
- Stimulation: Users choose too early or too late periods.
- Response: The system prompts too early or too late.
- Stimulus: User chooses to view historical portfolio recommendations.
- Response: The system displays portfolio recommendations for the corresponding time period.
- Stimulus: The user chooses to switch to a certain risk level
- Response: The system displays the portfolio recommendations for the corresponding time period under certain risk levels.

##### 3.2.5.3 Related Functional Requirements

| Functional Requirements         | Description                                                  |
| ------------------------------- | ------------------------------------------------------------ |
| 3.2.4 Portfolio recommendations | Comparison of recurrence needs to select the corresponding risk level. |

#### 3.2.6 Accessing System Detalis

##### 3.2.6.1 Characteristic decription

The system provides the users with a document of the details about the portfolio in a certain time period, which can be viewed in a new page or downloaded.

##### 3.2.6.2 Stimulus/Response Sequence

* Simulation: User clicks the data-analyst button. 
* Response: The system opens the fund portfolio details pdf file in a new tab.

#### 3.2.7 maintaining customer tracing blank

##### 3.2.7.1 Characteristic description

The system maintains the customer tracing blank base on user actions

##### 3.2.7.2 Stimulus/Response Sequence

- Simulation: User edit customer tracing blank
- Response: The system displays the blank after editing
- Simulation: User choose to save the blank
- Response: The system saves the blank

------

### 3.3 Non-functional Requirements

#### 3.3.1 Safety

* **Safety1**: There are no high security requirements for the current version of the system.

#### 3.3.2 Modifiability

* **Modifiability1**: The system must be able to support the development of further functionality.

#### 3.3.3 Usability

* **Usability1**: The system needs to be easily accessible to users who are slightly proficient in using computers.

#### 3.3.4 Reliability

* **Reliability1**: The system cannot crash during presentation.

#### 3.3.5 Business Rules

* **BR1**: Bank staff need to have access to customers' purchase and redemption records.
