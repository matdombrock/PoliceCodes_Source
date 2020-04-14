<template>
  <div class="hello">
    <h1>POLICE CODES</h1>
    <input type="text" placeholder="Search" v-model="search" @update="filter()">
    <br>
    <div class="table-wrap">
      <table class="table">
        <tr class="row" v-for="(code,index) in filtered" :key="index">
          <td class="name">{{code.name}}</td>
          <td class="meaning">{{code.meaning}}</td>
        </tr>
        <div class="no-results" v-if="filtered.length === 0">
          No Results For: "{{search}}" 
        </div>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Main',
  props: {
    msg: String
  },
  methods:{
    filter: function(){
      console.log(this.search);
    }
  },
  computed:{
    filtered:function(){
      const list = [];
      const search = this.search.toLowerCase();
      for(let code of this.codes){
        let hits = 0;
        const name = code.name.toLowerCase();
        const meaning = code.meaning.toLowerCase();
        if(name.includes(search)){
          hits++;
        }
        if(search.includes(name)){
          hits++;
        }

        if(meaning.includes(search)){
          hits++;
        }
        if(search.includes(meaning)){
          hits++;
        }
        if(hits>0){
          list.push(code);
        }
      }
      return list;
    }
  },
  data:function(){
    return {
      search: '',
      codes: [
        {
          name: '10-0',
          meaning: 'Use Caution'
        },
        {
          name: '10-1',
          meaning: 'Unable to copy - change location'
        },
        {
          name: '10-3',
          meaning: 'Stop transmitting'
        },
        {
          name: '10-4',
          meaning: 'Roger/Confirm/Okay'
        },
        {
          name: '10-5',
          meaning: 'Relay'
        },
        {
          name: '10-6',
          meaning: 'Busy'
        },
        {
          name: '10-7',
          meaning: 'Out at'
        },
        {
          name: '10-8',
          meaning: 'Clear'
        },
        {
          name: '10-9',
          meaning: 'Say again'
        },
        {
          name: '10-12',
          meaning: 'Stand by'
        },
        {
          name: '10-13',
          meaning: 'Weather report/Road report'
        },
        {
          name: '10-15',
          meaning: 'Disturbance'
        },
        {
          name: '10-17A',
          meaning: 'Theft'
        },
        {
          name: '10-17B',
          meaning: 'Vandalism'
        },
        {
          name: '10-17C',
          meaning: 'Shoplifting'
        },
        {
          name: '10-18',
          meaning: 'Urgent'
        },
        {
          name: '10-19',
          meaning: 'Return to'
        },
        {
          name: '10-20',
          meaning: 'Location'
        },
        {
          name: '10-21',
          meaning: 'Call'
        },
        {
          name: '10-22',
          meaning: 'Disregard'
        },
        {
          name: '10-23',
          meaning: 'On scene'
        },
        {
          name: '10-25',
          meaning: 'Meet/Contact'
        },
        {
          name: '10-26',
          meaning: 'Detaining subject'
        },
        {
          name: '10-27',
          meaning: 'Drivers license info'
        },
        {
          name: '10-28',
          meaning: 'Registration info'
        },
        {
          name: '10-29',
          meaning: 'Check wanted on'
        },
        {
          name: '10-31A',
          meaning: 'Burglary'
        },
        {
          name: '10-31B',
          meaning: 'Robbery'
        },
        {
          name: '10-31C',
          meaning: 'Homicide'
        },
        {
          name: '10-31D',
          meaning: 'Kidnapping'
        },
        {
          name: '10-31E',
          meaning: 'Shooting'
        },
        {
          name: '10-38',
          meaning: 'Traffic stop'
        },
        {
          name: '10-42',
          meaning: 'Off duty'
        },
        {
          name: '10-44',
          meaning: 'Request for'
        },
        {
          name: '10-46',
          meaning: 'Assist motorist'
        },
        {
          name: '10-49',
          meaning: 'Traffic light issue'
        },
        {
          name: '10-50',
          meaning: 'Traffic F=Fatal PD=Property Damage Hit and run Injury No injury reported Unknown Private property, location'
        },
        {
          name: '10-56',
          meaning: 'Drunk Pedestrian'
        },
        {
          name: '10-63',
          meaning: 'Prepare to copy'
        },
        {
          name: '10-70',
          meaning: 'Fire'
        },
        {
          name: '10-74',
          meaning: 'Negative'
        },
        {
          name: '10-76',
          meaning: 'En route'
        },
        {
          name: '10-77',
          meaning: 'ETA'
        },
        {
          name: '10-78',
          meaning: 'Request assistance'
        },
        {
          name: '10-79',
          meaning: 'Notify coroner'
        },
        {
          name: '10-80',
          meaning: 'Chase'
        },
        {
          name: '10-89',
          meaning: 'Bomb Threat'
        },
        {
          name: '10-90',
          meaning: 'Alarm'
        },
        {
          name: '10-91',
          meaning: 'Pickup Prisoner'
        },
        {
          name: '10-92',
          meaning: 'Parking complaint'
        },
        {
          name: '10-95',
          meaning: 'Prisoner in custody'
        },
        {
          name: '10-97',
          meaning: 'Check traffic signal'
        },
        {
          name: '10-98',
          meaning: 'Prison break/Jail break'
        },
        {
          name: '10-99',
          meaning: 'Wanted/Stolen'
        },
        // CLEAR SPEECH
        {
          name: 'CODE ONE(1)',
          meaning: 'Informs all units to STANDBY - STOP TRANSMITTING. Do not transmit, except for emergency messages, while Code 1 is in effect. Dispatch shall announce, “Clear Code 1,” when the condition is secured.'
        },
        {
          name: 'CODE TWO(2)',
          meaning: 'Indicates an “urgent” call short of an “emergency” situation. A Code 2 call has priority over all other police activities except “emergencies”. Proceed directly to Code 2 calls as quickly as is consistent with safety. Agents may, in exceptional cases, use their emergency equipment (both visual and audible to comply with state law) to traverse an otherwise clear intersection against a red traffic control device. Once clear of the intersection - turn off the emergency equipment.'
        },
        {
          name: 'CODE THREE(3)',
          meaning: 'Indicates an EMERGENCY call. Red lights and siren are authorized. Proceed as quickly as possible with due regard for safety, and in compliance with the laws governing emergency vehicles.'
        },
        {
          name: 'CODE FOUR(4)',
          meaning: 'Used to indicate that sufficient units have responded to a location, or that assistance is not needed, or is no longer needed.'
        },
        {
          name: 'CODE FIVE(5)',
          meaning: 'Used when Wanted/Records checks are requested by an agent to alert the agent of a wanted felon, a person known to be dangerous or a person known to be mentally unstable. A backup unit shall be dispatched Code 2 on all Code 5’s. Personnel will NOT proceed with Code 5 details until the receiving unit requests same. The unit receiving a Code 5 will request the details when he is in a safe position to do so, which might not be until his backup arrives.'
        },
        {
          name: 'CODE SIX(6)',
          meaning: 'When an agent is dispatched to a traffic accident, and the dispatcher states, “Code 6,” the agent will advise the drivers involved to proceed to the station to file their reports. This will only be done if there are no injuries, no unusual circumstance and the vehicles are safely operable. Driver Exchange Forms will be completed at the scene to include the C. R. number.'
        },
        {
          name: 'CODE SEVEN(7)',
          meaning: 'Indicates “out of service - personal.”'
        },
        {
          name: 'CODE EIGHT(8)',
          meaning: 'Assist a fire department.'
        },
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1{
  height:5vh;
  padding:1.5rem;
  margin:0 auto;
}
.table-wrap{
  overflow-y: scroll;
  width:50vw;
  max-width:800px;
  margin:0 auto;
  flex-grow : 1;
  max-height:80vh;
}
.table{
  text-align:left;
}
.name, .meaning{
  padding:0.5rem;
}
.name{
  max-width:100px;
  min-width:75px;
  width:5vw;
  font-weight: bolder;
  text-transform: uppercase;
  background: var(--accent1);
}
.meaning{
  background: var(--accent2);
  width:100%;
}
.no-results{
  padding:1rem;
}
@media only screen and (max-width: 800px) {
  .table-wrap{
    width:100vw;
  }
}
input{
  background:var(--accent1);
  color:var(--color);
  border-style: none;
  font-size:2rem;
  padding:0.25rem;
  width:50vw;
  max-width:800px;
  height:5vh;
}
@media only screen and (max-width: 800px) {
  input{
    width:95.5vw;
  }
}

</style>
