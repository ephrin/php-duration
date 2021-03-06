# PHP-Duration
## Converts between colon formatted time, human-readable time and seconds

I wanted an easy way for users to input how long something took, as a duration of time.

The library can accept either in colon separated format, like 2:43 for 2 minutes and 43 seconds
OR
written as human readable or abbreviated time, such as 6m21s for 6 minutes and 21 seconds.

Both can be converted into seconds for easy storage into a database.

Seconds, colon separated, abbreviated, all three can be parsed and interchanged.
 - supports hours, minutes, and seconds
 - humanized input supports any form of the words "hour", "minute", "seconds"
   - Example, you could input 1h4m2s or 4 Hr. 32 Min.


# Install
```
composer require khill/php-duration:~1.0
```


# Usage
```
use Khill\Duration\Duration;


$duration = new Duration('7:31');

echo $duration->humanize();  // 7m 31s
echo $duration->formatted(); // 7:31
echo $duration->toSeconds(); // 451
```

```
$duration = new Duration('1h 2m 5s');

echo $duration->humanize();  // 1h 2m 5s
echo $duration->formatted(); // 1:02:05
echo $duration->toSeconds(); // 3725
```

```
$duration = new Duration('4293');

echo $duration->humanize();  // 1h 11m 33s
echo $duration->formatted(); // 1:11:33
echo $duration->toSeconds(); // 4293
```

# Note
You do not have to create a new object for each conversion, you can also pass any of the three forms into any of the methods to get the immediate output.
```
$duration = new Duration;

echo $duration->humanize('1h 2m 5s');  // 1h 2m 5s
echo $duration->formatted('1h 2m 5s'); // 1:02:05
echo $duration->toSeconds('1h 2m 5s'); // 3725
```