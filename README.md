# current-weather-data
Display the current weather data for any location.

Input the City, State in the script below to grab the temperature from the Yahoo weather API

### Step 1

```
      $(document).ready(function() {

        var apiquery = escape('select * from weather.forecast where woeid in (select woeid from geo.places(1) where text="Yuma, AZ")');
        var url = 'https://query.yahooapis.com/v1/public/yql?q='+apiquery+'&format=json&env='+escape("store://datatables.org/alltableswithkeys");

        $.ajax({
          url: url,
          dataType : 'json',
          success : function(data) {
            $("#weather").html(data.query.results.channel.item.condition.temp + '&deg;F');
          }
        });

      });

```
