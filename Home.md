

```dataviewjs

function getNumberOfDaysInYear() {
  const currentDate = new Date();
  const currentYear = currentDate.getFullYear();

  // Leap year check: if divisible by 4 and not divisible by 100, or divisible by 400
  const isLeapYear = (currentYear % 4 === 0 && currentYear % 100 !== 0) || (currentYear % 400 === 0);

  // Number of days in a non-leap year and a leap year
  const daysInNonLeapYear = 365;
  const daysInLeapYear = 366;

  return isLeapYear ? daysInLeapYear : daysInNonLeapYear;
}

function getCurrentDayIndexInYear() {
  const currentDate = new Date();
  const startOfYear = new Date(currentDate.getFullYear(), 0, 0);
  const timeDiff = currentDate - startOfYear;
  const dayIndex = Math.floor(timeDiff / (24 * 60 * 60 * 1000));

  return dayIndex;
}

const days = getNumberOfDaysInYear();
const current = getCurrentDayIndexInYear();
const progress = Math.floor((current / days) * 1000) / 10;

dv.paragraph(`Year progress: day ${current} of ${days} (${progress}%)`);
dv.paragraph(`<progress max=${days} value=${current} style="width: 100%"></progress>`)
```

Some links or another main content here

---

# ✅ Tasks

***
# <mark class="hltr-green" style="display: block; width: 100%">Today</mark>

```tasks
filter by function !task.isDone
due on or before today
group by function task.file.path.split('/')[1]
sort by priority
```

###### <mark class="hltr-grey">Show completed tasks</mark>

```tasks
done today
filter by function task.isDone
group by function task.file.path.split('/')[1]
sort by priority
```

# <mark class="hltr-orange" style="display: block; width: 100%">Tomorrow</mark>

```tasks
filter by function !task.isDone
due tomorrow
group by function task.file.path.split('/')[1]
sort by priority
```

# <mark class="hltr-blue" style="display: block; width: 100%">Planned</mark>

```tasks
filter by function !task.isDone
filter by function task.due.moment?.isSameOrAfter(moment().add(2, 'days'), 'day') ?? false
group by function task.file.path.split('/')[1]
sort by priority
```

# <mark class="hltr-purple" style="display: block; width: 100%">Someday</mark>

```tasks
filter by function !task.isDone
no due date
group by function task.file.path.split('/')[1]
sort by priority
```
