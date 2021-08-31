## About this repository
[demo-care](https://demo-care.herokuapp.com/) is a simple react application that provides an overview of observations
between caregivers and **care recipients** (older adults).

These could be anything from the recording of their mood (happy, sad, bored, confused) to what they drank today (1 pint of water).

Each of these observations are recorded as events. Here's an example of a mood observation recorded
in this event format:

``` json
{  
   "id":"decaa026-2ce5-49cb-aff9-92326b85a98c",
   "event_type":"mood_observation",
   "visit_id":"39b94aab-cc35-4874-807f-c23472aec663",
   "timestamp":"2019-04-23T10:53:13+01:00",
   "caregiver_id":"4786d616-259e-4d52-80f7-8cf7dc6d881a",
   "care_recipient_id":"03f3306d-a4a3-4179-ab88-81af66df8b7c",
   "mood":"okay",
},
```

Here's a quick explanation of the base properties:

- `id`: Uniquely identifies the observation.
- `event_type`: Title we use to categorise our events.
- `visit_id`: Observations are traditionally observed during a visit between the caregiver (carer) and care recipient. This ID identifies that visit.
- `caregiver_id`: Identifies who the caregiver (carer) was that made this observation.
- `care_recipient_id`: Identifies the care recipient this observation is for.

On top of that, there can be **additional properties** based on the `event_type`:

- `mood` describes the mood of the care recipient as reported by the caregiver

## Set up

Here's the technical this application was made with:

### Front end
- [React](https://reactjs.org/)
- [Redux](https://redux.js.org/introduction/getting-started)

### Back end

- [Express](https://expressjs.com/)
- [MySQL](https://www.mysql.com/)
- [Node.js](https://nodejs.org/)
- [Sequelize](https://sequelize.org/)
## Usage

1. Clone the repository with the following command
   
   ```bash
   git clone --recursive https://github.com/Abdul-Qoyyum/demo-care.git
   ```
2. Set up your database credentials   (Do the following within the `backend` folder)

   a. Generate `.env` file
    
   ```bash
   yarn gen:env
   ```
   b. Set up database credentials in the .env file.  


3. Start the API. (Run the following commands within the `backend` folder)

   a. Install the dependencies

   ```bash
   yarn install
   ```
   b. Run migration
   
   ```bash
   yarn migrate
   ```
   
   c. Populate the database with dummy data

   ```bash
     yarn db:seed
   ```

   d. Run the HTTP server (will start on port `8000`)

   ```bash
   yarn dev
   ```
4. Start the React app  (Run the following commands within the `front-end` folder)

    a. Generate `.env` file

    ```bash
     yarn gen:env
    ```
   
    b. Install the dependencies

   ```bash
   yarn install
   ```

   c. Run the application (will start on port `3000`)

   ```bash
   yarn start
   ```

## Test
1. Do the following within the backend folder.

   a. Set up test database credentials in the `.env` file
   
```bash
   #DB for testing
   CI_DB_HOST="localhost"
   CI_DB_DATABASE="care_development"
   CI_DB_USERNAME="root"
   CI_DB_PASSWORD=""
   #one of 'mysql' | 'mariadb' | 'postgres' | 'mssql'
   CI_DB_DIALECT="mysql"
```
  b. Run
```bash
   yarn test
```
