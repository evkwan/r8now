<script lang="ts">
    import moment from 'moment';
  import { copy } from '../locale/en';

    const  randomMinMaxInt = (min, max) =>  Math.floor(Math.random() * (max - min + 1) + min);
    const mmt = moment();
    const dayOfTheYear = mmt.dayOfYear();
    const weekOfTheYear = mmt.isoWeek();
    const year = mmt.year();
    const daysInYear = mmt.isLeapYear() ? 366 : 365;
    const daysLeftInYear = daysInYear - dayOfTheYear;
    const quarter = mmt.quarter();
    const isLastQ = quarter === 4 ? true : false;
    const nextQuarter = isLastQ ? 4 : quarter + 1;
    const nextQuarterStartDate = moment(`${year}-01-01T00:00:00.000`).quarter(nextQuarter);
    const daysToNextQ = isLastQ ? daysLeftInYear : moment.duration(nextQuarterStartDate.diff(mmt.startOf('day'))).asDays();
    const copyKey = 'q' + quarter;
    const copyForQ = copy[copyKey];
    const lengthOfCopy = Object.keys(copyForQ).length;
    const randomKey = randomMinMaxInt(1, lengthOfCopy);

</script>

<main>
    <h2><span class="day">Day {dayOfTheYear}</span>, <span class="week">Week {weekOfTheYear}</span> of Year <span class="year">{year}<span/> </h2>
    <div>
            <h3>{daysToNextQ} days left to { isLastQ ? 'the end of Q4' :  `Q${nextQuarter} ${year}`}</h3>
            <h3>{daysLeftInYear} days left in the year</h3>
    </div>
    <div class="quote"> {copyForQ[`0${randomKey}`]} </div>
</main>

<style></style>