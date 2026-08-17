# BPMN Exercise 1

This repository contains BPMN models for three business process scenarios created using Camunda Modeler.

---

# Scenario 1: Employee Leave Approval

![Employee Leave Approval BPMN](https://github.com/user-attachments/assets/888ae31d-f411-4f07-92ed-877fbe8eaf8a)

### Process Description

An employee applies for leave through the HR system. The system first checks whether the employee has enough leave balance before routing the request to a manager for a decision.

### Flow Logic

1. **Start Event** – "Employee Submits Leave Request" triggers the process.
2. **Task** – "Check Leave Balance": the HR system verifies the available leave balance.
3. **Exclusive Gateway** – "Sufficient Balance?"

   * **No** → **Task** "Send Insufficient Balance Notification" → **End Event** "Insufficient Balance".
   * **Yes** → **Task** "Send Request to Manager for Approval".
4. **Exclusive Gateway** – "Manager Approves?"

   * **Approved** → **Task** "Update Employee Leave Balance" → **Task** "Send Approval Notification" → **End Event** "Leave Approved".
   * **Rejected** → **Task** "Send Rejection Notification" → **End Event** "Leave Rejected".

---

# Scenario 2: Online Purchase Order Processing

![Online Purchase Order Processing BPMN](https://github.com/user-attachments/assets/3fb7e4ff-90ba-4360-84ba-a7ede4c1a4a0)

### Process Description

A customer places an online order. The system checks product availability and processes payment before confirming and shipping the order.

### Flow Logic

1. **Start Event** – "Customer Places Order".
2. **Task** – "Check Product Availability".
3. **Exclusive Gateway** – "Product Available?"

   * **No** → **Task** "Notify Customer - Out of Stock" → **End Event** "Out of Stock".
   * **Yes** → **Task** "Process Payment".
4. **Exclusive Gateway** – "Payment Successful?"

   * **No** → **Task** "Notify Customer - Payment Failed" → **End Event** "Payment Failed".
   * **Yes** → **Task** "Confirm Order" → **Task** "Prepare Product for Shipment" → **Task** "Ship Order" → **Task** "Send Shipping Confirmation" → **End Event** "Order Completed".

---

# Scenario 3: IT Service Request

![IT Service Request BPMN](https://github.com/user-attachments/assets/ba42cf51-8a55-41d5-b0fd-62a0472bbead)

### Process Description

An employee reports an IT problem. The help desk registers and triages it by severity, assigns it to the appropriate technician tier, and routes it internally or externally depending on whether it can be resolved in-house.

### Flow Logic

1. **Start Event** – "Employee Reports IT Problem".
2. **Task** – "Submit IT Support Request".
3. **Task** – "Register Request": the help desk logs the ticket.
4. **Task** – "Check Severity of the Problem".
5. **Exclusive Gateway** – "Severity Level?"

   * **Low Severity** → **Task** "Assign to Support Technician".
   * **High Severity** → **Task** "Assign to Senior Technician".
   * Both paths **converge** at a merging Exclusive Gateway before continuing.
6. **Task** – "Investigate the Problem".
7. **Exclusive Gateway** – "Resolvable Internally?"

   * **Yes** → **Task** "Fix the Problem".
   * **No** → **Task** "Escalate to External Service Provider".
   * Both paths **converge** again at a second merging Exclusive Gateway.
8. **Task** – "Update Request Status".
9. **Task** – "Send Resolution Notification to Employee".
10. **End Event** – "Request Resolved".

---

## BPMN Elements Used

* **Start Event** – Indicates the beginning of a process.
* **Task** – Represents an activity performed during the process.
* **Exclusive Gateway** – Represents a decision where one path is selected.
* **Sequence Flow** – Connects BPMN elements and shows the direction of the process.
* **End Event** – Indicates the completion of a process.

## Tools Used

* **Camunda Modeler**
* **BPMN 2.0**
* **GitHub**
