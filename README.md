# IIT BBS BasBandhu

*"Never miss your shuttle again."*

A live campus bus timetable for IIT Bhubaneswar. Pick where you are and where you are going, and see the next bus with a countdown, plus every departure for the day. The schedule follows the Transport Office notice.

## Features

- **From and To pickers** with a swap button and an "Anywhere" option. Stop codes show their full names (Administrative Building, Ganga Hall of Residence and so on).
- **Next bus panel** with a live countdown and vehicle numbers, refreshed every 15 seconds, and a live clock.
- **Mon to Sat and Sun/Holiday schedules**, with today's one selected automatically.
- **Route filters:** all routes, campus shuttle, city and campus, and Niser Square.
- **Clear departure list:** buses leaving within 15 minutes are highlighted, buses that have already left are greyed out, and faculty/officers-only trips are marked.
- **Direction aware:** a bus is only listed if your From stop comes before your To stop on its route.
- **Bus-horn intro** with a driving animation. Animations switch off for visitors who prefer reduced motion.

The time shown is when a bus starts its route. If your stop isn't the first one, the bus reaches you a little later.

## Tech

- One self-contained `index.html`: plain HTML, CSS and vanilla JavaScript. No framework, no build step, no backend.
- Google Fonts (Baloo 2 and JetBrains Mono).
- `bus-horn.mp3` for the intro sound.

## Run it

Open `index.html` in a browser, or serve the folder locally:

```bash
python -m http.server 8000
```

Then visit `http://localhost:8000`. It can be hosted on any static host (Netlify, Vercel, GitHub Pages).

## Updating the schedule

All timetable data sits at the top of the `<script>` block in `index.html`, in six lists:

`shuttleWeekday`, `shuttleSunday`, `cityWeekday`, `citySunday`, `niserWeekday` and `niserSunday`.

Each row has the same shape (times are 24-hour):

```js
['08:50', 'GHR-ABB-LHL(P)-AB-SIF', ['B4']]
```

The three parts are the start time, the stops in order joined with `-`, and the vehicles. City rows have a fourth value, `true` for faculty/officers only and `false` otherwise.

For a new notice:

1. Replace the rows in those lists.
2. Add any new stop codes and their full names to `STOP_NAMES`.
3. Update the "Schedule valid until" line in the header and the dates in the comment above the data.

## Credits

Built by Sriram G. 
Schedule data from the IIT Bhubaneswar Transport Office notice.
