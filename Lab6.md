# Lab 6
# Lớp phân tích

         
1. Maintain Timecard Subsystem

    1. Lớp Boundary : TimecardForm
        + Phương thức:
            displayTimecard(): void
            enterHours(): void
            displayChargeCodes(): void
            saveTimecard(): void
    2. Lớp Controller : TimecardController
        + Phương thức:
            getCurrentTimecard(forEmployee: Employee): Timecard
            getChargeNums(): ChargeNumList
            updateTimecard(withEntry: TimecardEntry): void
            saveTimecard(): void
    3. Lớp Entity : IProjectManagementDatabase
        + Phương thức:
            getChargeNumbers(criteria: String): ChargeNumList
    4. Lớp Entity : ChargeNumList
        + Phương thức:
            create(): void
            add(): void
            delete(): void
    5. Lớp Entity : Timecard
        + Phương thức:
            getTotalHours(): float
            updateTimecard(entry: TimecardEntry): void
            save(): void
    6. Lớp Entity : TimecardEntry
        + Thuộc tính:
            dayOfWeek: String
            numHours: float
    7. Lớp Entity : PayPeriod
        + Thuộc tính:
            startDate: Date
            endDate: Date
    8. Lớp Entity : Employee
        + Phương thức:
            add(timecard: Timecard): void
            getEmployeeID(): int
   ![Diagram](https://planttext.com/api/plantuml/png/Z5IzJiCm4Dxp5Dv81rwWGXKYWAZ4JoMGc8_u6WnENDaEAAfu4YPM5dOwCF0aVG9UWOiRkqcR8hB4kSztzzrtT_bPV1qQ2zgMkOpssFboyJfZDoB753G_LJfdyP4g2mww6aIf16Eww3nYz71XPX8gZyG3PyN2eZvJfJQDeRcMt8FEC54SFM3W2LlEBz4MbKGLLYifKREuEM_oQLrPiShG9gNMH2F4dYfzai-agX27p9y6R1Y214V7yRBCYIB1uVDS6Elkb3CETatwMTZx4yfVhKEvpzhvIGdUKwP7MjME9rezO6ele80CSs9-31Rkm22BnxMQKqXn40b__CjXlbNA7L8dKYt8MS2GNLijYcoxkXQV3i1YgaZOC0TTS9KkrKYgD5q5xYU1eqHdxkdiPjXW3mNSA0kocIDYEvKAUdk0_z6_LtS_2PjSWdqU2h9Dz7MUJWgYwvt6nouNDQklRCTkL-qhiDajgAwcjuYFpBVCcOioTv84GLev9b1DgCTgIziri8hjDfyc1YbA_MhMbhTDBcxo_POoARxV2_Qu_FooB1FBnGUmrDdhf57djx2_F-hPowXdLTitT-5UqLruTtvtNFfZLORiuA0qE1e5tmujruqk58IC3ack-j_v2m00__y30000)         2. Payroll Processing Subsystem
   
       - Lớp thiết kế : PayrollController (Control)
          + Thuộc tính:
              payrolls: List<Paycheck>
          + Phương thức:
              calculatePayroll(timecard: Timecard, employee: Employee): Paycheck
              processPayroll(employeeID: String): void
       - Lớp thiết kế : Paycheck (Entity)       
          + Thuộc tính:
              paycheckID: String
              employeeID: String
              amount: Float
              issueDate: Date
          + Phương thức:
              generatePayStub(): String
       - Lớp thiết kế : PayrollDatabase (Entity)
          + Thuộc tính:
              payrollRecords: List<Paycheck>
          + Phương thức:
              savePaycheck(paycheck: Paycheck): void
       - Lớp thiết kế : BankSystemProxy (Boundary)
          + Thuộc tính:
              bankDetails: BankInformation
          + Phương thức:
              transferSalary(paycheck: Paycheck): Boolean
![Diagran](https://planttext.com/api/plantuml/png/T591QiCm4Bph5NkB2_K7J0c1KEYXbD0KUXRorXMH9IF9WL3wafvwxQNt-f13Nk8Nz0kL52d4ZgkBbfdLx32htsw_C9PgszQ2p22F1nvR2Ikwqqg84qYOeCOaUAcazJTgU2FWZcvbfB86DLTbuLjNeRo20hQAbw6nGecQMdIi4RmncMVlkR4t4PcJTp8SjaQzvGpZ94O5QyLH8SEw4Mg7MC1jhAx1yXePrSx1KwpyY1UXg0q2ZLOCZV7F9wt-RyOZqKKQ_41hT6_MLdDP7UMJ5fpf1iOgIyMTQhLvLdg3vS1L85t_01o5bPsITAvci3nyCX3yy2LXq__iBLIyxxufi83ttKS3x5MTRvDShY_FvwESoIXstv7IdU9IobDSD4vIU16BeInGbkxh_G400F__0m00)
3. Bank System
   
![Diagram](https://planttext.com/api/plantuml/png/j5EnQkGm4Etz5TET36j2YgGGOSab9108uI1RNAlLQcsnihH8un0J3W8fKwM-vdBN7HntzRf8iI7_uVn0VY7AxjhnUdrbN1WnysRUUpFII_6mxv1Pp58LV8BJilW-XGEc9-UvGv4UAYaq0ZamcHuncuS1LyovJSHL0FuRYQbn4icKvJmHV4BXo-hKWw4lET5ZOrE6qcYwwD48XC6te4C1a4EZqHgbXDra_mZUWMNQCVwM0tAaKUAQxMPwoSwjO2Z8IiGWdmeAvsYbZdl0KZyvf31MXc4FhCdGny-oT2XiXGeNNLmsJBs5DJcLYxQEEhuK40lylE0X8QoesgOQXhjCDTFBdcjAePBQlQCJZSAE6HT0wcCOo3hQXRngciRtcTBsaAk1oFbl3PDoze0GoxBuou3FxpceDot1ndsCedxpcj3wYeGDR8rgxfHM-zn0rbEdiBUNET7lT_Lg6wNlcsrJ_QUa4rUH1_j2Z_nZVRw-tTwbspjRaVElGyTRKIByCwPzQcX428qI-EfLeNtwvoV4OP98YClYZnmavUmN74ib75pCVnXul9l_pFs_B6xWqfUeSdOlEmfV0G00__y30000)

