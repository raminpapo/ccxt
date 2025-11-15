# Documentation: cs/ccxt/static/StarkSharp/StarkSharp.Tools/Sharp.Update/SharpUpdate.cs

## File Metadata

- **Path**: `cs/ccxt/static/StarkSharp/StarkSharp.Tools/Sharp.Update/SharpUpdate.cs`
- **Size**: 1,437 bytes
- **Lines**: 57
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Collections.Generic;
using System.Timers;

namespace StarkSharp.Tools.SharpUpdate
{

    public class SharpUpdateTask
    {
        public Action Action;
        public float Time, Timer;

        public SharpUpdateTask(Action action, float time)
        {
            Time = time;
            Action = action;
            Timer = time;
        }
    }

    public class SharpUpdate
    {
        private List<SharpUpdateTask> tasks = new List<SharpUpdateTask>();
        private System.Timers.Timer timer;
        private float targetTickRate = 1f / 10f;

        public SharpUpdate()
        {
            timer = new System.Timers.Timer(targetTickRate * 1000);
            timer.Elapsed += OnTimedEvent;
            timer.AutoReset = true;
            timer.Enabled = true;
        }

        public void AddTask(Action action, float time)
        {
            tasks.Add(new SharpUpdateTask(action, time));
        }

        private void OnTimedEvent(object source, ElapsedEventArgs e)
        {
            foreach (SharpUpdateTask task in tasks) HandleTask(task);
        }

        private void HandleTask(SharpUpdateTask task)
        {
            task.Timer -= targetTickRate;
            if (task.Timer > 0) return;
            task.Action.Invoke();
            task.Timer = task.Time;
        }

        public void Start() => timer.Start();

        public void Stop() => timer.Stop();
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/StarkSharp/StarkSharp.Tools/Sharp.Update/SharpUpdate.cs`.

**Classes defined**: SharpUpdateTask, SharpUpdate



## Detailed Walkthrough

### Code Structure

- Total lines: 57
- Code lines: 47
- Comment lines: 0
- Blank lines: 10

### Main Components

**Classes** (2):
- `SharpUpdate`
- `SharpUpdateTask`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

