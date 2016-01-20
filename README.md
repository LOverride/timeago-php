# timeago in PHP
Using [http://php.net/manual/en/function.time.php](http://php.net/manual/en/function.time.php) to determinate time ago

```
function get_timeago($time){
  $estimate_time = time() - strtotime($time);

    if($estimate_time < 1)
      return 'less than 1 second ago';

    $condition = array( 
      12 * 30 * 24 * 60 * 60  =>  'year',
      30 * 24 * 60 * 60       =>  'month',
      24 * 60 * 60            =>  'day',
      60 * 60                 =>  'hour',
      60                      =>  'minute',
      1                       =>  'second'
    );

    foreach($condition as $secs => $str){
        $d = $estimate_time / $secs;

        if($d >= 1){
            $r = round($d);
            return 'about ' . $r . ' ' . $str . ( $r > 1 ? 's' : '' ) . ' ago';
        }
    }
}

get_timeago("2016-01-19 05:18:43");
```
