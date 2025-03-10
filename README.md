# async_task_scheduler

`async_task_scheduler` is a Python module that allows you to schedule asynchronous tasks using various scheduling strategies such as cron-like schedules, one-time execution, and more.

## Installation

To install the module, simply install it using `pip`:

```sh
pip install async_task_scheduler
```

## Usage

### Creating a Scheduler

First, create an instance of the `Scheduler` class:

```python
from async_task_scheduler import Scheduler

scheduler = Scheduler()
```

### Adding Tasks

You can add tasks to the scheduler using various decorators:

#### Always

Runs the task every minute.

```python
@scheduler.always
async def print_time_every_minute():
    print("Cron time:", datetime.now().strftime("%M %H %d %m %w"))
```

#### Cron

Runs the task based on a cron-like schedule.

```python
@scheduler.cron("*/2 * * * *")
async def two_minutes():
    print("Every 2 minutes")
```

#### Hourly

Runs the task at the start of every hour.

```python
@scheduler.hourly
async def hourly_task():
    print("It is now", datetime.now().strftime("%H:%M"))
```

#### Daily

Runs the task at the start of every day.

```python
@scheduler.daily
async def daily_task():
    print("Good morning!")
```

#### Weekly

Runs the task at the start of every week.

```python
@scheduler.weekly
async def weekly_task():
    print("This is a weekly task!")
```

#### Monthly

Runs the task at the start of every month.

```python
@scheduler.monthly
async def monthly_task():
    print("Welcome to", datetime.now().strftime("%B"))
```

#### At Start

Runs the task once when the scheduler starts.

```python
@scheduler.at_start
async def long_task():
    print("Long task starting")
    await asyncio.sleep(5)
    print("Long task done")
```

#### At Specific Time

Runs the task at a specific datetime.

```python
@scheduler.at(datetime(2025, 3, 10, 18, 29))
async def future_task():
    print("This is a task for a specific time.")
```

### Running the Scheduler

To run the scheduler, await the `run` method or call it using `asyncio.run`:

```python
await scheduler.run()
```

or

```python
asyncio.run(scheduler.run())
```

The scheduler will run indefinitely until the program is stopped.

## Example

See the end of the source file for a complete example.

## License

This project is licensed under the MIT License.
