# AvaWorkflow Complete Tutorial

This comprehensive tutorial will guide you through all aspects of using AvaWorkflow, from basic concepts to advanced features.

## Table of Contents

1. [Introduction](#introduction)
2. [Understanding Workflows](#understanding-workflows)
3. [Getting Started](#getting-started)
4. [Creating Your First Workflow](#creating-your-first-workflow)
5. [Working with Activities](#working-with-activities)
6. [Advanced Features](#advanced-features)
7. [Best Practices](#best-practices)
8. [Troubleshooting](#troubleshooting)

## Introduction

AvaWorkflow is a visual workflow designer that allows you to create, edit, and execute workflows using an intuitive drag-and-drop interface. Built on Avalonia UI, it provides a consistent experience across Windows, macOS, and Linux.

### What is a Workflow?

A workflow is a sequence of activities that are executed in a specific order to accomplish a task. Workflows can include:

- **Sequential steps**: Activities executed one after another
- **Parallel branches**: Multiple activities running simultaneously
- **Conditional logic**: Decision points that direct flow based on conditions
- **Loops**: Repeating activities multiple times

## Understanding Workflows

### Core Concepts

#### Activities
Activities are the building blocks of workflows. Each activity represents a single unit of work, such as:
- Processing data
- Making decisions
- Calling external services
- Transforming information

#### Connections
Connections define the flow between activities. They determine the execution order and can carry data between activities.

#### Variables
Variables store data that can be used across activities in a workflow. They support various data types including strings, numbers, booleans, and complex objects.

#### Expressions
Expressions are used to compute values dynamically. They can reference variables, perform calculations, and make decisions.

## Getting Started

### Main Interface Overview

![Main Interface](images/main-interface.png)

The AvaWorkflow interface consists of several key areas:

1. **Menu Bar**: Access to file operations, editing tools, and settings
2. **Toolbar**: Quick access to common actions
3. **Activity Toolbox**: Available activities that can be added to workflows
4. **Canvas**: The main area where you design your workflow
5. **Properties Panel**: Configure selected activities
6. **Status Bar**: Displays workflow status and notifications

### Keyboard Shortcuts

| Action | Windows/Linux | macOS |
|--------|---------------|-------|
| New Workflow | Ctrl+N | Cmd+N |
| Open Workflow | Ctrl+O | Cmd+O |
| Save Workflow | Ctrl+S | Cmd+S |
| Run Workflow | F5 | F5 |
| Stop Workflow | Shift+F5 | Shift+F5 |
| Delete Selected | Delete | Delete |
| Undo | Ctrl+Z | Cmd+Z |
| Redo | Ctrl+Y | Cmd+Y |

## Creating Your First Workflow

Let's create a simple workflow that processes data and saves the results.

### Step 1: Create a New Workflow

1. Launch AvaWorkflow
2. Select **File** → **New Workflow**
3. Enter "My First Workflow" as the name
4. Click **Create**

![Step 1: Create New Workflow](images/step1-create-workflow.png)

### Step 2: Add Activities

We'll add four activities to create a basic workflow:

1. **Start Activity**: Marks the beginning of the workflow
2. **Process Data Activity**: Simulates data processing
3. **Save Result Activity**: Saves the processed data
4. **End Activity**: Marks the completion of the workflow

To add each activity:
1. Locate it in the Activity Toolbox
2. Drag it onto the canvas
3. Position it where you want

![Step 2: Add Workflow Activities](images/step2-add-activities.png)

**Activity Toolbox Categories:**

- **Control Flow**: Start, End, Decision, Loop
- **Data**: Transform, Filter, Aggregate
- **I/O**: Read File, Write File, HTTP Request
- **Custom**: User-defined activities

### Step 3: Connect Activities

Now we'll connect the activities to define the execution flow:

1. Click the **output connector** (small circle on the right) of the Start activity
2. Drag your mouse to the **input connector** (small circle on the left) of the Process Data activity
3. Release to create the connection
4. Repeat to connect:
   - Process Data → Save Result
   - Save Result → End

![Step 3: Connect Activities](images/step3-connect-activities.png)

**Connection Tips:**
- Hold Shift while dragging to create straight connections
- Click a connection to select it (turns blue)
- Press Delete to remove a selected connection
- Connections show data flow direction with arrows

### Step 4: Configure Activity Properties

Select each activity and configure its properties:

#### Process Data Activity

1. Click on the Process Data activity to select it
2. In the Properties Panel:
   - **Name**: `ProcessData`
   - **Timeout**: `30s`
   - **Retry Count**: `3`
   - **Input Data**: `${inputData}`
   - **Output Variable**: `${processedData}`

![Step 4: Configure Activity Properties](images/step4-configure-properties.png)

#### Save Result Activity

1. Select the Save Result activity
2. Configure:
   - **Name**: `SaveResult`
   - **Input**: `${processedData}`
   - **File Path**: `output.txt`

**Property Types:**

- **Text**: Simple string values
- **Number**: Integer or decimal values
- **Boolean**: True/false values
- **Expression**: Dynamic values using `${...}` syntax
- **Object**: Complex JSON objects

### Step 5: Run and Monitor the Workflow

Now let's execute the workflow:

1. Click the **Run** button (▶️) in the toolbar or press F5
2. Watch the activities execute in sequence
3. The Execution Monitor shows the status of each activity

![Step 5: Run and Monitor Workflow](images/step5-run-workflow.png)

**Status Indicators:**

- ✓ **Green (Completed)**: Activity finished successfully
- ⟳ **Yellow (Running)**: Activity is currently executing
- ○ **Gray (Pending)**: Activity is waiting to execute
- ✗ **Red (Failed)**: Activity encountered an error

## Working with Activities

### Built-in Activities

#### Control Flow Activities

**Start Activity**
- Marks the entry point of the workflow
- Every workflow must have exactly one Start activity
- No configuration required

**End Activity**
- Marks the terminal point of the workflow
- Workflows can have multiple End activities
- Terminates execution when reached

**Decision Activity**
- Creates conditional branches in the workflow
- Evaluates an expression and routes to True or False path
- Configuration:
  - **Condition**: Expression that evaluates to true/false
  - **True Path**: Connection when condition is true
  - **False Path**: Connection when condition is false

**Loop Activity**
- Repeats a set of activities
- Types:
  - **For Each**: Iterate over a collection
  - **While**: Repeat while condition is true
  - **Do While**: Execute at least once, then repeat while condition is true
- Configuration:
  - **Collection/Condition**: What to iterate over or check
  - **Loop Variable**: Variable to store current item
  - **Max Iterations**: Safety limit to prevent infinite loops

#### Data Activities

**Transform Activity**
- Converts data from one format to another
- Supports multiple transformation types:
  - String manipulation (uppercase, lowercase, trim)
  - Number operations (round, floor, ceil)
  - Date formatting
  - JSON parsing/serialization

**Filter Activity**
- Filters collections based on conditions
- Configuration:
  - **Input Collection**: Source data
  - **Filter Expression**: Condition for filtering
  - **Output Variable**: Where to store filtered results

**Aggregate Activity**
- Performs calculations on collections
- Supported operations:
  - Sum, Average, Min, Max
  - Count, Distinct
  - Group By

#### I/O Activities

**Read File Activity**
- Reads content from a file
- Configuration:
  - **File Path**: Path to the file
  - **Encoding**: File encoding (UTF-8, ASCII, etc.)
  - **Output Variable**: Where to store file content

**Write File Activity**
- Writes content to a file
- Configuration:
  - **File Path**: Destination path
  - **Content**: Data to write (can use expressions)
  - **Append**: Whether to append or overwrite

**HTTP Request Activity**
- Makes HTTP/HTTPS requests
- Configuration:
  - **URL**: Endpoint URL
  - **Method**: GET, POST, PUT, DELETE, etc.
  - **Headers**: Request headers
  - **Body**: Request body (for POST/PUT)
  - **Output Variable**: Where to store response

### Creating Custom Activities

You can extend AvaWorkflow with custom activities:

```csharp
public class MyCustomActivity : ActivityBase
{
    [ActivityProperty("Input Data")]
    public string InputData { get; set; }
    
    [ActivityProperty("Output Variable")]
    public string OutputVariable { get; set; }
    
    public override async Task<ActivityResult> ExecuteAsync(WorkflowContext context)
    {
        // Your custom logic here
        var result = ProcessData(InputData);
        
        context.Variables[OutputVariable] = result;
        
        return ActivityResult.Success();
    }
    
    private string ProcessData(string input)
    {
        // Implementation
        return input.ToUpper();
    }
}
```

## Advanced Features

### Variables and Expressions

#### Variable Scope

Variables can have different scopes:
- **Workflow-level**: Available to all activities
- **Activity-level**: Only available within an activity
- **Loop-level**: Available within a loop

#### Expression Syntax

```javascript
// Variable reference
${myVariable}

// Property access
${user.name}

// Array access
${items[0]}

// Arithmetic
${count + 1}
${price * quantity}

// Comparison
${age >= 18}
${status == "active"}

// Logical operators
${isValid && isActive}
${condition1 || condition2}

// String operations
${firstName + " " + lastName}
${message.ToUpper()}

// Function calls
${Math.Round(value, 2)}
${DateTime.Now}
```

### Error Handling

#### Retry Configuration

Configure automatic retries for activities:
- **Retry Count**: Number of retry attempts
- **Retry Delay**: Wait time between retries
- **Exponential Backoff**: Increase delay with each retry

#### Error Handling Strategies

1. **Try-Catch Pattern**: Use Decision activities to check for errors
2. **Compensation**: Define activities to undo previous work
3. **Dead Letter Queue**: Route failed items to a separate queue

### Parallel Execution

Run multiple activities simultaneously:

1. Create multiple output connections from a single activity
2. Activities on different paths execute in parallel
3. Use a **Join Activity** to synchronize completion

### Workflow Versioning

AvaWorkflow supports workflow versioning:
- Save different versions of the same workflow
- Track changes over time
- Roll back to previous versions if needed

## Best Practices

### Design Principles

1. **Keep it Simple**: Break complex workflows into smaller, manageable pieces
2. **Reuse Components**: Create reusable sub-workflows for common patterns
3. **Error Handling**: Always plan for failure scenarios
4. **Documentation**: Use descriptive names and add comments

### Performance Tips

1. **Avoid Deep Nesting**: Limit the depth of nested loops and decisions
2. **Use Parallel Execution**: Run independent activities in parallel
3. **Optimize Data Access**: Minimize file I/O and network calls
4. **Set Timeouts**: Always set appropriate timeout values

### Testing Workflows

1. **Unit Test Activities**: Test individual activities separately
2. **Integration Testing**: Test complete workflows
3. **Edge Cases**: Test with boundary conditions and error scenarios
4. **Performance Testing**: Measure execution time under load

### Security Considerations

1. **Validate Input**: Always validate data from external sources
2. **Secure Credentials**: Use secure storage for passwords and API keys
3. **Access Control**: Implement proper authorization
4. **Audit Logging**: Track workflow execution for compliance

## Troubleshooting

### Common Issues

#### Workflow Won't Start

**Symptoms**: Run button is disabled or nothing happens when clicked

**Solutions**:
1. Check for validation errors (shown in red)
2. Ensure the workflow has a Start activity
3. Verify all required properties are configured
4. Check for disconnected activities

#### Activity Timeout

**Symptoms**: Activity shows timeout error

**Solutions**:
1. Increase the timeout value
2. Optimize the activity logic
3. Check for network issues (for I/O activities)
4. Review retry configuration

#### Variable Not Found

**Symptoms**: Expression error: variable not defined

**Solutions**:
1. Check variable name spelling
2. Verify the variable is set before use
3. Check variable scope
4. Initialize variables before first use

#### Infinite Loop

**Symptoms**: Workflow runs indefinitely

**Solutions**:
1. Check loop conditions
2. Set maximum iteration limits
3. Ensure loop variables are modified
4. Use the Stop button to halt execution

### Debug Mode

Enable debug mode for detailed execution information:

1. Click **View** → **Debug Mode**
2. Set breakpoints on activities
3. Step through execution one activity at a time
4. Inspect variable values at each step

### Logs and Diagnostics

Access execution logs:

1. Click **View** → **Execution Logs**
2. Filter by severity: Info, Warning, Error
3. Export logs for analysis
4. Enable verbose logging for detailed output

## Conclusion

You now have a comprehensive understanding of AvaWorkflow! Continue exploring the application to discover more features and capabilities.

For additional resources:
- [API Documentation](API.md)
- [Examples](examples/)
- [Community Forum](https://github.com/JimmyKodu/AvaWorkflow/discussions)
- [Issue Tracker](https://github.com/JimmyKodu/AvaWorkflow/issues)

Happy workflow designing! 🎉
