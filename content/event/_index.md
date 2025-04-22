---
title: Upcoming Events

# Listing view
view: compact

# Optional header image (relative to `assets/media/` folder).
banner:
  caption: ''
  image: ''

---
<br />
<span style="font-size: 12pt;"><em>Interested in attending our lab meetings? These meetings are open to all students at UKE and usually take place on Wednesday mornings at 11:00 in SFB-Raum W34. If you are interested in attending, please contact us in advance so that we can ensure adequate space</em></span><br><br>

<script src="//ajax.googleapis.com/ajax/libs/jquery/1.7.1/jquery.min.js"></script>
<script>
    function arrayToTable(tableData) {
      console.log(tableData)
      console.log('arrayToTable function triggered')
      var table = $('<div class="event-table"></div>')
      console.log(table)
      for (const i in tableData) {
        var rowData = tableData[i]
        var row = $('<div class="event-row"></div>')
        // extract the dates 
        var dateStr = rowData.Date;
        if (dateStr !== '') {
          console.log(dateStr)
          const dateParts = dateStr.split(".");
          const date = new Date(dateParts[2], dateParts[1] - 1, dateParts[0]);
          const dayOfWeek = date.toLocaleString("en-US", { weekday: "short" });
          const month = date.toLocaleString("en-US", { month: "short" });
          const day = date.getDate();
          const formattedDate = `<b>${day}</b> <span style="font-size: 10pt; font-variant-caps: small-caps;">${month}, <em>${dayOfWeek}</em></span> `;
          var event_date = $('<div class="event-row-date">'+formattedDate+'</div>')
        } else {
          var event_date = $('<div class="event-row-date"></div>')
        }
        row.append(event_date)
        // now we include the rest of the details 
        var row_details = $(`<div class="event-row-details" onclick="toggleDetails('`+sanitise(rowData.Description)+`')"></div>`)
        var timeStr = rowData.Time;
        if (timeStr !== '') {
          const timeParts = timeStr.split(":");
          const hours = parseInt(timeParts[0]);
          const minutes = timeParts[1];
          const formattedTime = getFormattedTime(hours, minutes);
          var event_time = $('<div class="event-row-time">'+formattedTime+'</div>')
        } else {
          var event_time = $('<div class="event-row-time-empty"></div>')
        }
        row_details.append(event_time)
        var presenter = rowData.Who;
        var event_title = $('<div class="event-row-title">'+presenter+'</div>')
        row_details.append(event_title)
        if (rowData.Location !== '') {
          var event_loc = $('<div class="event-row-location">'+rowData.Location+'</div>')
          row_details.append(event_loc)
        } 
        row.append(row_details)
        table.append(row)
      }
      console.log(table)
      return table;
    }
    function sanitise(string) {
      const map = {
          '&': '&amp;',
          '<': '&lt;',
          '>': '&gt;',
          '"': '&quot;',
          "'": '&#x27;',
          "/": '&#x2F;',
          ",": '&#44;',
      };
      const reg = /[&<>"'/]/ig;
      return string.replace(reg, (match)=>(map[match]));
    }
    function toggleDetails(description) { 
      console.log('Toggling the popup')
      var popup = document.getElementById('event-details-popup');
      if (description !== '') {
        popup.innerHTML = '<span class="event-notes">'+description+'</span>';
      } else {
        popup.innerHTML = '<span class="event-notes">This meeting will involve a presentation by a lab member and is open to visitors. Please get in touch if you would like more information</span>';
      }
      popup.classList.toggle('show')
    }
    function getFormattedTime(hours, minutes) {
      const ampm = hours < 12 ? "am" : "pm";
      hours = hours % 12;
      if (hours === 0) {
        hours = 12;
      }
      return `${hours}${minutes === "00" ? "" : `:${minutes}`}${ampm}`;
    }
    function csvToJson(csvData) {
      var lines = csvData.split("\n");
      var headers = lines[0].split(",");
      var jsonData = [];
      for (var i = 1; i < lines.length; i++) {
        var obj = {};
        var line = lines[i].split(",");
        for (var j = 0; j < headers.length; j++) {
          obj[headers[j].trim()] = line[j].trim();
        }
        jsonData.push(obj);
      }
      return jsonData;
    }
    $.ajax({
        type: "GET",
        url: "https://docs.google.com/spreadsheets/d/e/2PACX-1vQI1N_CUatG--9q0EH0gqwhEik2M85aiEXWX9pXekQoeFDOCHY1SvXo2gb5RFozTCk7M-CLJ4ztskw-/pub?gid=0&single=true&output=csv",
        success: function (data) {
          $('.article-style').append(arrayToTable(csvToJson(data)));
        }
    });
</script>

<div class="popup"><span class="popuptext" id="event-details-popup"></span></div>

