## Re-Evaluate Risk Tolerance Using JSON Data and Financial Analysis with AutoGen


### Project Overview

This project aims to reevaluate risk tolerance based on user-provided financial and demographic data stored in JSON format. The project processes this data, analyzes financial goals, and generates updated risk tolerance values using **Microsoft Autogen** (or a similar framework). The code allows flexibility to use predefined or custom frameworks to carry out the task.

### Project Structure

- **Financial Data Loading**: The solution reads a JSON file (`userForm.json`) that contains detailed user information, including:
  - **Demographics**: Age, gender, occupation, etc.
  - **Financials**: Income, debt, insurance, etc.
  - **Retirement plans**: Expected retirement age, future lifestyle, etc.
  - **Investment Goals**: Time horizon and specific financial goals.
  - **Risk Tolerance**: Initial investment, target value, and time interval.
  - **Investment Strategy and Portfolio**: Asset distribution among debt, equity, and hybrid funds.

- **OLLAMA API**: is used to download the **Mistral AI model** onto the local system. The **Mistral model** is hosted locally as a server using **Litellm**, which allows efficient deployment of large language models on personal infrastructure.
- **Microsoft Autogen**: is configured to subscribe to the locally hosted Mistral model via the Litellm server. The agent leverages this model to analyze financial data, reassess risk tolerance, and perform the necessary tasks autonomously.

- **Autonomous Financial Agents**: Multiple agents (`autogen.AssistantAgent`) such as the `FinancialGoalsAgent`, `InvestmentStrategyAgent` and the `PortfolioStructureAgent` were used to processes the financial information based on criteria such as Financial goals, Investment strategy and Portfolio Structure respectively. With this information the Agent uses a pre-configured large language model (LLM) to analyze user data and deliver a detailed financial assessment and reassesses the risk tolerance levels.
  
- **Reassessment of Risk Tolerance**: The agent calculates updated risk tolerance by examining the current financial setup and future goals, ensuring that the user's portfolio strategy aligns with their financial objectives.

- **JSON Output**: The new risk tolerance values are written back to a JSON file, making the data easy to integrate into other financial systems or services.
  
### Getting Started

#### Prerequisites

- **Python 3.x** installed.
- **Jupyter Notebook** environment.
- Required libraries:
  - `json` for handling JSON data.
  - `autogen` for leveraging the Microsoft Autogen framework (or a similar framework) to create autonomous agents.

#### How to Run

1. **Install dependencies**:
   If the required libraries are not installed, you can install them using the following:
   ```bash
   pip install autogen json
   ```

2. **Run the notebook**:
   Open the `Autogen_Risk_Tolerance.ipynb` file in Jupyter Notebook and run the cells sequentially.

3. **Input JSON File**:
   Make sure that a valid `userForm.json` file is present in the working directory. This file should contain structured financial data.

4. **Run the Agent**:
   The autonomous agent will analyze the data and output the reassessed risk tolerance. The results will be saved in a new JSON file.

### Example JSON Structure

The input JSON file (`userForm.json`) should follow this structure:

```json
{
    "userDetails": {
        "demographics": {
            "age": 25,
            "gender": "Male",
            "occupation": "Software Engineer"
        },
        "financials": {
            "income": 1000000,
            "investments": ["Real Estate"],
            "debt": 100000,
            "insurance": 50000
        },
        "retirementPlans": {
            "retirementAge": 35,
            "lifeStyle": ["Buy a new house"]
        },
        "financialGoals": {
            "timeDuration": 10,
            "investmentGoals": ["Buy a new house"]
        },
        "riskTolerance": {
            "initialInvestment": 1000000,
            "targetValue": 2000000,
            "timeInterval": 10
        },
        "investmentStrategy": {
            "option": "Target value"
        },
        "portfolioStructure": {
            "equity": ["Diversified Equity Funds"],
            "debt": [],
            "hybrid": []
        }
    }
}
```

### Customization

This project can be adapted to different financial frameworks by:
- Modifying the **Autogen framework** configuration to interact with different LLM models or services.
- Extending the analysis by incorporating additional financial data fields or using more complex financial algorithms.

### Future Improvements

- Adding support for different financial models and strategies.
- Increasing the sophistication of risk tolerance reassessment using historical financial data and real-time market conditions.
- Integration with other financial tools and APIs for live data updates.
