# Event-Calender
Calender for Event mangement
<h2>Browser Support</h2>
<table>
<thead>
<tr>
<th><a href="http://godban.github.io/browsers-support-badges/" rel="nofollow"><img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/firefox/firefox_48x48.png" alt="Firefox" width="24px" height="24px" style="max-width:100%;"></a><br>Firefox</th>
<th><a href="http://godban.github.io/browsers-support-badges/" rel="nofollow"><img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/chrome/chrome_48x48.png" alt="Chrome" width="24px" height="24px" style="max-width:100%;"></a><br>Chrome</th>
<th><a href="http://godban.github.io/browsers-support-badges/" rel="nofollow"><img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/safari/safari_48x48.png" alt="Safari" width="24px" height="24px" style="max-width:100%;"></a><br>Safari</th>
<th><a href="http://godban.github.io/browsers-support-badges/" rel="nofollow"><img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/edge/edge_48x48.png" alt="Edge" width="24px" height="24px" style="max-width:100%;"></a><br> Edge</th>
<th><a href="http://godban.github.io/browsers-support-badges/" rel="nofollow"><img src="https://camo.githubusercontent.com/bee1cc9f16d2b46e860ef2f3660273f98302c9ab/68747470733a2f2f75706c6f61642e77696b696d656469612e6f72672f77696b6970656469612f636f6d6d6f6e732f312f31622f496e7465726e65745f4578706c6f7265725f395f69636f6e2e737667" alt="IE" width="24px" height="24px" data-canonical-src="https://upload.wikimedia.org/wikipedia/commons/1/1b/Internet_Explorer_9_icon.svg" style="max-width:100%;"></a><br> IE11</th>
</tr>
</thead>
<tbody>
<tr>
<td>31+ ✔</td>
<td>35+ ✔</td>
<td>6+ ✔</td>
<td>Edge ✔</td>
<td><a href="#using-it-with-ie11">(IE11)</a> ✔</td>
</tr>
</tbody>
</table>
<h2>Download and Installation</h2>
<h5>Installing via GIT</h5>
<div class="highlight highlight-source-shell"><pre>git clone https://github.com/keyur4200/Event-Calender-.git</pre></div>
<h5>Direct <script> Include</h5>
<div class="highlight highlight-source-shell"><pre>Direct include screept boot_cal.js in your project</pre></div>
<h2>Usage</h2>
<div class="highlight highlight-source-shell">
  <pre>
  var calendar = $('#calendar').fullCalendar({
            header: {
                left: 'title',
                center: 'agendaDay,agendaWeek,month',
                right: 'prev,next today'
            },
            editable: true,
            firstDay: 0,
            selectable: true,
            defaultView: 'month',
            axisFormat: 'h:mm',
            columnFormat: {
                month: 'ddd',
                week: 'ddd d',
                day: 'dddd M/d',
                agendaDay: 'dddd d'
            },
            titleFormat: {
                month: 'MMMM yyyy',
                week: "MMMM yyyy",
                day: 'MMMM yyyy'
            },
            allDaySlot: true,
            selectHelper: true,
            select: function(start, end, allDay) {
                var title = prompt('Event Title:');
                if (title) {
                    calendar.fullCalendar('renderEvent', {
                            title: title,
                            start: start,
                            end: end,
                            allDay: allDay
                        },
                        true
                    );
                }
                calendar.fullCalendar('unselect');
            },
            droppable: true,
            drop: function(date, allDay) {

                var originalEventObject = $(this).data('eventObject');

                var copiedEventObject = $.extend({}, originalEventObject);

                copiedEventObject.start = date;
                copiedEventObject.allDay = allDay;


                $('#calendar').fullCalendar('renderEvent', copiedEventObject, true);

                if ($('#drop-remove').is(':checked')) {

                    $(this).remove();
                }
            },
            events: [{
                    title: 'All Day Event',
                    start: new Date(y, m, 1)
                },
                {
                    id: 999,
                    title: 'Repeating Event',
                    start: new Date(y, m, d - 3, 16, 0),
                    allDay: false,
                    className: 'info1'
                },
                {
                    id: 99,
                    title: 'Repeating Event',
                    start: new Date(y, m, d + 4, 16, 0),
                    allDay: false,
                    className: 'info'
                },

                {
                    title: 'Birthday Party',
                    start: new Date(y, m, d + 1, 19, 0),
                    end: new Date(y, m, d + 1, 22, 30),
                    allDay: false,
                },
                {
                    title: 'Meeting',
                    start: new Date(y, m, d, 10, 0),
                    end: new Date(y, m, d, 10, 60),
                    allDay: false,
                    className: 'important'
                },
                {
                    title: 'Lunch',
                    start: new Date(y, m, d, 12, 0),
                    end: new Date(y, m, d, 14, 0),
                    allDay: false,
                    className: 'important'
                },
                {
                    title: 'Click for Google',
                    start: new Date(y, m, 28),
                    end: new Date(y, m, 29),
                    url: 'https://www.google.com',
                    className: 'success'
                }
            ],
        });
  </pre>
  </div>
