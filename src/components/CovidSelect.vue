<template>
  <ion-grid>
    <div v-if="isSrchShow">
      <ion-toolbar>
        <!-- :value="country" -->
        <ion-searchbar
          ref="srchInput"
          placeholder="Enter Country Name"
          @ionChange="cntryChng($event.target.value)"
        ></ion-searchbar>
      </ion-toolbar>
      <ion-card class="listView" v-if="list && list.length > 0">
        <ion-content class="lviewChild" fullscreen="false">
          <ion-item
            class="hvrItem"
            v-for="cntry in list"
            v-bind:key="cntry.id"
            v-on:click="itemClick(cntry.key);"
          >{{cntry.name}}</ion-item>
        </ion-content>
      </ion-card>
      <div class="cstmRow">
        <ion-button
          shape="round"
          class="cstmBtn"
          size="default"
          v-on:click="OnSubmit()"
          color="primary"
        >Find</ion-button>
        <ion-button
          shape="round"
          class="cstmBtn"
          size="default"
          v-on:click="OnSubmit();"
          color="medium"
        >Clear</ion-button>
      </div>
    </div>
    <div class="cstmRow" v-if="!isSrchShow">
      <ion-button
        shape="round"
        class="cstmBtn"
        size="default"
        v-on:click="OnSubmit(null, 'reset')"
        color="primary"
      >Try New Country</ion-button>
    </div>
    <!-- <form @submit="OnSubmit">
      <ion-select
        :value="country"
        @ionChange="country = $event.target.value"
        name="country"
        placeholder="Select Country"
      >
        <ion-select-option value="AFG">Afghanistan</ion-select-option>
        <ion-select-option value="ALB">Albania</ion-select-option>
        <ion-select-option value="DZA">Algeria</ion-select-option>
        <ion-select-option value="AND">Andorra</ion-select-option>
        <ion-select-option value="AGO">Angola</ion-select-option>
        <ion-select-option value="AIA">Anguilla</ion-select-option>
        <ion-select-option value="ATG">Antigua and Barbuda</ion-select-option>
        <ion-select-option value="ARG">Argentina</ion-select-option>
        <ion-select-option value="ARM">Armenia</ion-select-option>
        <ion-select-option value="ABW">Aruba</ion-select-option>
        <ion-select-option value="AUS">Australia</ion-select-option>
        <ion-select-option value="AUT">Austria</ion-select-option>
        <ion-select-option value="AZE">Azerbaijan</ion-select-option>
        <ion-select-option value="BHS">Bahamas</ion-select-option>
        <ion-select-option value="BHR">Bahrain</ion-select-option>
        <ion-select-option value="BGD">Bangladesh</ion-select-option>
        <ion-select-option value="BRB">Barbados</ion-select-option>
        <ion-select-option value="BLR">Belarus</ion-select-option>
        <ion-select-option value="BEL">Belgium</ion-select-option>
        <ion-select-option value="BLZ">Belize</ion-select-option>
        <ion-select-option value="BEN">Benin</ion-select-option>
        <ion-select-option value="BMU">Bermuda</ion-select-option>
        <ion-select-option value="BTN">Bhutan</ion-select-option>
        <ion-select-option value="BOL">Bolivia</ion-select-option>
        <ion-select-option value="BIH">Bosnia</ion-select-option>
        <ion-select-option value="BRA">Brazil</ion-select-option>
        <ion-select-option value="VGB">British Virgin Islands</ion-select-option>
        <ion-select-option value="BRN">Brunei</ion-select-option>
        <ion-select-option value="BGR">Bulgaria</ion-select-option>
        <ion-select-option value="BFA">Burkina Faso</ion-select-option>
        <ion-select-option value="CPV">Cabo Verde</ion-select-option>
        <ion-select-option value="KHM">Cambodia</ion-select-option>
        <ion-select-option value="CMR">Cameroon</ion-select-option>
        <ion-select-option value="CAN">Canada</ion-select-option>
        <ion-select-option value="CYM">Cayman Islands</ion-select-option>
        <ion-select-option value="CAF">Central African Republic</ion-select-option>
        <ion-select-option value="TCD">Chad</ion-select-option>
        <ion-select-option value="JEY">Channel Islands</ion-select-option>
        <ion-select-option value="CHL">Chile</ion-select-option>
        <ion-select-option value="CHN">China</ion-select-option>
        <ion-select-option value="COL">Colombia</ion-select-option>
        <ion-select-option value="COG">Congo</ion-select-option>
        <ion-select-option value="COD">Congo the Democratic Republic of the</ion-select-option>
        <ion-select-option value="CRI">Costa Rica</ion-select-option>
        <ion-select-option value="CIV">Côte d'Ivoire</ion-select-option>
        <ion-select-option value="HRV">Croatia</ion-select-option>
        <ion-select-option value="CUB">Cuba</ion-select-option>
        <ion-select-option value="CUW">Curacao</ion-select-option>
        <ion-select-option value="CYP">Cyprus</ion-select-option>
        <ion-select-option value="CZE">Czechia</ion-select-option>
        <ion-select-option value="DNK">Denmark</ion-select-option>
        <ion-select-option value="null">Diamond Princess</ion-select-option>
        <ion-select-option value="DJI">Djibouti</ion-select-option>
        <ion-select-option value="DMA">Dominica</ion-select-option>
        <ion-select-option value="DOM">Dominican Republic</ion-select-option>
        <ion-select-option value="ECU">Ecuador</ion-select-option>
        <ion-select-option value="EGY">Egypt</ion-select-option>
        <ion-select-option value="SLV">El Salvador</ion-select-option>
        <ion-select-option value="GNQ">Equatorial Guinea</ion-select-option>
        <ion-select-option value="ERI">Eritrea</ion-select-option>
        <ion-select-option value="EST">Estonia</ion-select-option>
        <ion-select-option value="ETH">Ethiopia</ion-select-option>
        <ion-select-option value="FRO">Faroe Islands</ion-select-option>
        <ion-select-option value="FJI">Fiji</ion-select-option>
        <ion-select-option value="FIN">Finland</ion-select-option>
        <ion-select-option value="FRA">France</ion-select-option>
        <ion-select-option value="GUF">French Guiana</ion-select-option>
        <ion-select-option value="PYF">French Polynesia</ion-select-option>
        <ion-select-option value="GAB">Gabon</ion-select-option>
        <ion-select-option value="GMB">Gambia</ion-select-option>
        <ion-select-option value="GEO">Georgia</ion-select-option>
        <ion-select-option value="DEU">Germany</ion-select-option>
        <ion-select-option value="GHA">Ghana</ion-select-option>
        <ion-select-option value="GIB">Gibraltar</ion-select-option>
        <ion-select-option value="GRC">Greece</ion-select-option>
        <ion-select-option value="GRL">Greenland</ion-select-option>
        <ion-select-option value="GRD">Grenada</ion-select-option>
        <ion-select-option value="GLP">Guadeloupe</ion-select-option>
        <ion-select-option value="GTM">Guatemala</ion-select-option>
        <ion-select-option value="GIN">Guinea</ion-select-option>
        <ion-select-option value="GNB">Guinea-Bissau</ion-select-option>
        <ion-select-option value="GUY">Guyana</ion-select-option>
        <ion-select-option value="HTI">Haiti</ion-select-option>
        <ion-select-option value="VAT">Holy See (Vatican City State)</ion-select-option>
        <ion-select-option value="HND">Honduras</ion-select-option>
        <ion-select-option value="HKG">Hong Kong</ion-select-option>
        <ion-select-option value="HUN">Hungary</ion-select-option>
        <ion-select-option value="ISL">Iceland</ion-select-option>
        <ion-select-option value="IND">India</ion-select-option>
        <ion-select-option value="IDN">Indonesia</ion-select-option>
        <ion-select-option value="IRN">Iran</ion-select-option>
        <ion-select-option value="IRQ">Iraq</ion-select-option>
        <ion-select-option value="IRL">Ireland</ion-select-option>
        <ion-select-option value="IMN">Isle of Man</ion-select-option>
        <ion-select-option value="ISR">Israel</ion-select-option>
        <ion-select-option value="ITA">Italy</ion-select-option>
        <ion-select-option value="JAM">Jamaica</ion-select-option>
        <ion-select-option value="JPN">Japan</ion-select-option>
        <ion-select-option value="JOR">Jordan</ion-select-option>
        <ion-select-option value="KAZ">Kazakhstan</ion-select-option>
        <ion-select-option value="KEN">Kenya</ion-select-option>
        <ion-select-option value="KWT">Kuwait</ion-select-option>
        <ion-select-option value="KGZ">Kyrgyzstan</ion-select-option>
        <ion-select-option value="LAO">Lao People's Democratic Republic</ion-select-option>
        <ion-select-option value="LVA">Latvia</ion-select-option>
        <ion-select-option value="LBN">Lebanon</ion-select-option>
        <ion-select-option value="LBR">Liberia</ion-select-option>
        <ion-select-option value="LBY">Libyan Arab Jamahiriya</ion-select-option>
        <ion-select-option value="LIE">Liechtenstein</ion-select-option>
        <ion-select-option value="LTU">Lithuania</ion-select-option>
        <ion-select-option value="LUX">Luxembourg</ion-select-option>
        <ion-select-option value="MAC">Macao</ion-select-option>
        <ion-select-option value="MKD">Macedonia</ion-select-option>
        <ion-select-option value="MDG">Madagascar</ion-select-option>
        <ion-select-option value="MYS">Malaysia</ion-select-option>
        <ion-select-option value="MDV">Maldives</ion-select-option>
        <ion-select-option value="MLI">Mali</ion-select-option>
        <ion-select-option value="MLT">Malta</ion-select-option>
        <ion-select-option value="MTQ">Martinique</ion-select-option>
        <ion-select-option value="MRT">Mauritania</ion-select-option>
        <ion-select-option value="MUS">Mauritius</ion-select-option>
        <ion-select-option value="MYT">Mayotte</ion-select-option>
        <ion-select-option value="MEX">Mexico</ion-select-option>
        <ion-select-option value="MDA">Moldova Republic of</ion-select-option>
        <ion-select-option value="MCO">Monaco</ion-select-option>
        <ion-select-option value="MNG">Mongolia</ion-select-option>
        <ion-select-option value="MNE">Montenegro</ion-select-option>
        <ion-select-option value="MSR">Montserrat</ion-select-option>
        <ion-select-option value="MAR">Morocco</ion-select-option>
        <ion-select-option value="MOZ">Mozambique</ion-select-option>
        <ion-select-option value="null">MS Zaandam</ion-select-option>
        <ion-select-option value="MMR">Myanmar</ion-select-option>
        <ion-select-option value="NAM">Namibia</ion-select-option>
        <ion-select-option value="NPL">Nepal</ion-select-option>
        <ion-select-option value="NLD">Netherlands</ion-select-option>
        <ion-select-option value="NCL">New Caledonia</ion-select-option>
        <ion-select-option value="NZL">New Zealand</ion-select-option>
        <ion-select-option value="NIC">Nicaragua</ion-select-option>
        <ion-select-option value="NER">Niger</ion-select-option>
        <ion-select-option value="NGA">Nigeria</ion-select-option>
        <ion-select-option value="NOR">Norway</ion-select-option>
        <ion-select-option value="OMN">Oman</ion-select-option>
        <ion-select-option value="PAK">Pakistan</ion-select-option>
        <ion-select-option value="PSE">Palestinian Territory Occupied</ion-select-option>
        <ion-select-option value="PAN">Panama</ion-select-option>
        <ion-select-option value="PNG">Papua New Guinea</ion-select-option>
        <ion-select-option value="PRY">Paraguay</ion-select-option>
        <ion-select-option value="PER">Peru</ion-select-option>
        <ion-select-option value="PHL">Philippines</ion-select-option>
        <ion-select-option value="POL">Poland</ion-select-option>
        <ion-select-option value="PRT">Portugal</ion-select-option>
        <ion-select-option value="QAT">Qatar</ion-select-option>
        <ion-select-option value="REU">Réunion</ion-select-option>
        <ion-select-option value="ROU">Romania</ion-select-option>
        <ion-select-option value="RUS">Russia</ion-select-option>
        <ion-select-option value="RWA">Rwanda</ion-select-option>
        <ion-select-option value="KOR">S. Korea</ion-select-option>
        <ion-select-option value="KNA">Saint Kitts and Nevis</ion-select-option>
        <ion-select-option value="LCA">Saint Lucia</ion-select-option>
        <ion-select-option value="MAF">Saint Martin</ion-select-option>
        <ion-select-option value="VCT">Saint Vincent and the Grenadines</ion-select-option>
        <ion-select-option value="SMR">San Marino</ion-select-option>
        <ion-select-option value="SAU">Saudi Arabia</ion-select-option>
        <ion-select-option value="SEN">Senegal</ion-select-option>
        <ion-select-option value="SRB">Serbia</ion-select-option>
        <ion-select-option value="SYC">Seychelles</ion-select-option>
        <ion-select-option value="SGP">Singapore</ion-select-option>
        <ion-select-option value="SXM">Sint Maarten</ion-select-option>
        <ion-select-option value="SVK">Slovakia</ion-select-option>
        <ion-select-option value="SVN">Slovenia</ion-select-option>
        <ion-select-option value="SOM">Somalia</ion-select-option>
        <ion-select-option value="ZAF">South Africa</ion-select-option>
        <ion-select-option value="ESP">Spain</ion-select-option>
        <ion-select-option value="LKA">Sri Lanka</ion-select-option>
        <ion-select-option value="BLM">St. Barth</ion-select-option>
        <ion-select-option value="SDN">Sudan</ion-select-option>
        <ion-select-option value="SUR">Suriname</ion-select-option>
        <ion-select-option value="SWZ">Swaziland</ion-select-option>
        <ion-select-option value="SWE">Sweden</ion-select-option>
        <ion-select-option value="CHE">Switzerland</ion-select-option>
        <ion-select-option value="SYR">Syrian Arab Republic</ion-select-option>
        <ion-select-option value="TWN">Taiwan</ion-select-option>
        <ion-select-option value="TZA">Tanzania United Republic of</ion-select-option>
        <ion-select-option value="THA">Thailand</ion-select-option>
        <ion-select-option value="TLS">Timor-Leste</ion-select-option>
        <ion-select-option value="TGO">Togo</ion-select-option>
        <ion-select-option value="TTO">Trinidad and Tobago</ion-select-option>
        <ion-select-option value="TUN">Tunisia</ion-select-option>
        <ion-select-option value="TUR">Turkey</ion-select-option>
        <ion-select-option value="TCA">Turks and Caicos Islands</ion-select-option>
        <ion-select-option value="ARE">UAE</ion-select-option>
        <ion-select-option value="UGA">Uganda</ion-select-option>
        <ion-select-option value="GBR">UK</ion-select-option>
        <ion-select-option value="UKR">Ukraine</ion-select-option>
        <ion-select-option value="URY">Uruguay</ion-select-option>
        <ion-select-option value="USA">USA</ion-select-option>
        <ion-select-option value="UZB">Uzbekistan</ion-select-option>
        <ion-select-option value="VEN">Venezuela Bolivarian Republic of</ion-select-option>
        <ion-select-option value="VNM">Vietnam</ion-select-option>
        <ion-select-option value="ZMB">Zambia</ion-select-option>
        <ion-select-option value="ZWE">Zimbabwe</ion-select-option>
      </ion-select>
      <ion-button type="submit" color="primary" expand="block" round>Find</ion-button>
    </form>-->
  </ion-grid>
</template>
<script>

export default {
  name: "CovidSelect",
  data() {
    return {
      country: "",
      list: [],
      isSrchShow: true,
      srchVal: "",
      countries: [
        { key: "AFG", name: "Afghanistan" },
        { key: "ALB", name: "Albania" },
        { key: "DZA", name: "Algeria" },
        { key: "AND", name: "Andorra" },
        { key: "AGO", name: "Angola" },
        { key: "AIA", name: "Anguilla" },
        { key: "ATG", name: "Antigua and Barbuda" },
        { key: "ARG", name: "Argentina" },
        { key: "ARM", name: "Armenia" },
        { key: "ABW", name: "Aruba" },
        { key: "AUS", name: "Australia" },
        { key: "AUT", name: "Austria" },
        { key: "AZE", name: "Azerbaijan" },
        { key: "BHS", name: "Bahamas" },
        { key: "BHR", name: "Bahrain" },
        { key: "BGD", name: "Bangladesh" },
        { key: "BRB", name: "Barbados" },
        { key: "BLR", name: "Belarus" },
        { key: "BEL", name: "Belgium" },
        { key: "BLZ", name: "Belize" },
        { key: "BEN", name: "Benin" },
        { key: "BMU", name: "Bermuda" },
        { key: "BTN", name: "Bhutan" },
        { key: "BOL", name: "Bolivia" },
        { key: "BIH", name: "Bosnia" },
        { key: "BRA", name: "Brazil" },
        { key: "VGB", name: "British Virgin Islands" },
        { key: "BRN", name: "Brunei" },
        { key: "BGR", name: "Bulgaria" },
        { key: "BFA", name: "Burkina Faso" },
        { key: "CPV", name: "Cabo Verde" },
        { key: "KHM", name: "Cambodia" },
        { key: "CMR", name: "Cameroon" },
        { key: "CAN", name: "Canada" },
        { key: "CYM", name: "Cayman Islands" },
        { key: "CAF", name: "Central African Republic" },
        { key: "TCD", name: "Chad" },
        { key: "JEY", name: "Channel Islands" },
        { key: "CHL", name: "Chile" },
        { key: "CHN", name: "China" },
        { key: "COL", name: "Colombia" },
        { key: "COG", name: "Congo" },
        { key: "COD", name: "Congo the Democratic Republic of the" },
        { key: "CRI", name: "Costa Rica" },
        { key: "CIV", name: "Côte d'Ivoire" },
        { key: "HRV", name: "Croatia" },
        { key: "CUB", name: "Cuba" },
        { key: "CUW", name: "Curacao" },
        { key: "CYP", name: "Cyprus" },
        { key: "CZE", name: "Czechia" },
        { key: "DNK", name: "Denmark" },
        { key: "null", name: "Diamond Princess" },
        { key: "DJI", name: "Djibouti" },
        { key: "DMA", name: "Dominica" },
        { key: "DOM", name: "Dominican Republic" },
        { key: "ECU", name: "Ecuador" },
        { key: "EGY", name: "Egypt" },
        { key: "SLV", name: "El Salvador" },
        { key: "GNQ", name: "Equatorial Guinea" },
        { key: "ERI", name: "Eritrea" },
        { key: "EST", name: "Estonia" },
        { key: "ETH", name: "Ethiopia" },
        { key: "FRO", name: "Faroe Islands" },
        { key: "FJI", name: "Fiji" },
        { key: "FIN", name: "Finland" },
        { key: "FRA", name: "France" },
        { key: "GUF", name: "French Guiana" },
        { key: "PYF", name: "French Polynesia" },
        { key: "GAB", name: "Gabon" },
        { key: "GMB", name: "Gambia" },
        { key: "GEO", name: "Georgia" },
        { key: "DEU", name: "Germany" },
        { key: "GHA", name: "Ghana" },
        { key: "GIB", name: "Gibraltar" },
        { key: "GRC", name: "Greece" },
        { key: "GRL", name: "Greenland" },
        { key: "GRD", name: "Grenada" },
        { key: "GLP", name: "Guadeloupe" },
        { key: "GTM", name: "Guatemala" },
        { key: "GIN", name: "Guinea" },
        { key: "GNB", name: "Guinea-Bissau" },
        { key: "GUY", name: "Guyana" },
        { key: "HTI", name: "Haiti" },
        { key: "VAT", name: "Holy See (Vatican City State)" },
        { key: "HND", name: "Honduras" },
        { key: "HKG", name: "Hong Kong" },
        { key: "HUN", name: "Hungary" },
        { key: "ISL", name: "Iceland" },
        { key: "IND", name: "India" },
        { key: "IDN", name: "Indonesia" },
        { key: "IRN", name: "Iran" },
        { key: "IRQ", name: "Iraq" },
        { key: "IRL", name: "Ireland" },
        { key: "IMN", name: "Isle of Man" },
        { key: "ISR", name: "Israel" },
        { key: "ITA", name: "Italy" },
        { key: "JAM", name: "Jamaica" },
        { key: "JPN", name: "Japan" },
        { key: "JOR", name: "Jordan" },
        { key: "KAZ", name: "Kazakhstan" },
        { key: "KEN", name: "Kenya" },
        { key: "KWT", name: "Kuwait" },
        { key: "KGZ", name: "Kyrgyzstan" },
        { key: "LAO", name: "Lao People's Democratic Republic" },
        { key: "LVA", name: "Latvia" },
        { key: "LBN", name: "Lebanon" },
        { key: "LBR", name: "Liberia" },
        { key: "LBY", name: "Libyan Arab Jamahiriya" },
        { key: "LIE", name: "Liechtenstein" },
        { key: "LTU", name: "Lithuania" },
        { key: "LUX", name: "Luxembourg" },
        { key: "MAC", name: "Macao" },
        { key: "MKD", name: "Macedonia" },
        { key: "MDG", name: "Madagascar" },
        { key: "MYS", name: "Malaysia" },
        { key: "MDV", name: "Maldives" },
        { key: "MLI", name: "Mali" },
        { key: "MLT", name: "Malta" },
        { key: "MTQ", name: "Martinique" },
        { key: "MRT", name: "Mauritania" },
        { key: "MUS", name: "Mauritius" },
        { key: "MYT", name: "Mayotte" },
        { key: "MEX", name: "Mexico" },
        { key: "MDA", name: "Moldova Republic of" },
        { key: "MCO", name: "Monaco" },
        { key: "MNG", name: "Mongolia" },
        { key: "MNE", name: "Montenegro" },
        { key: "MSR", name: "Montserrat" },
        { key: "MAR", name: "Morocco" },
        { key: "MOZ", name: "Mozambique" },
        { key: "null", name: "MS Zaandam" },
        { key: "MMR", name: "Myanmar" },
        { key: "NAM", name: "Namibia" },
        { key: "NPL", name: "Nepal" },
        { key: "NLD", name: "Netherlands" },
        { key: "NCL", name: "New Caledonia" },
        { key: "NZL", name: "New Zealand" },
        { key: "NIC", name: "Nicaragua" },
        { key: "NER", name: "Niger" },
        { key: "NGA", name: "Nigeria" },
        { key: "NOR", name: "Norway" },
        { key: "OMN", name: "Oman" },
        { key: "PAK", name: "Pakistan" },
        { key: "PSE", name: "Palestinian Territory Occupied" },
        { key: "PAN", name: "Panama" },
        { key: "PNG", name: "Papua New Guinea" },
        { key: "PRY", name: "Paraguay" },
        { key: "PER", name: "Peru" },
        { key: "PHL", name: "Philippines" },
        { key: "POL", name: "Poland" },
        { key: "PRT", name: "Portugal" },
        { key: "QAT", name: "Qatar" },
        { key: "REU", name: "Réunion" },
        { key: "ROU", name: "Romania" },
        { key: "RUS", name: "Russia" },
        { key: "RWA", name: "Rwanda" },
        { key: "KOR", name: "S. Korea" },
        { key: "KNA", name: "Saint Kitts and Nevis" },
        { key: "LCA", name: "Saint Lucia" },
        { key: "MAF", name: "Saint Martin" },
        { key: "VCT", name: "Saint Vincent and the Grenadines" },
        { key: "SMR", name: "San Marino" },
        { key: "SAU", name: "Saudi Arabia" },
        { key: "SEN", name: "Senegal" },
        { key: "SRB", name: "Serbia" },
        { key: "SYC", name: "Seychelles" },
        { key: "SGP", name: "Singapore" },
        { key: "SXM", name: "Sint Maarten" },
        { key: "SVK", name: "Slovakia" },
        { key: "SVN", name: "Slovenia" },
        { key: "SOM", name: "Somalia" },
        { key: "ZAF", name: "South Africa" },
        { key: "ESP", name: "Spain" },
        { key: "LKA", name: "Sri Lanka" },
        { key: "BLM", name: "St. Barth" },
        { key: "SDN", name: "Sudan" },
        { key: "SUR", name: "Suriname" },
        { key: "SWZ", name: "Swaziland" },
        { key: "SWE", name: "Sweden" },
        { key: "CHE", name: "Switzerland" },
        { key: "SYR", name: "Syrian Arab Republic" },
        { key: "TWN", name: "Taiwan" },
        { key: "TZA", name: "Tanzania United Republic of" },
        { key: "THA", name: "Thailand" },
        { key: "TLS", name: "Timor-Leste" },
        { key: "TGO", name: "Togo" },
        { key: "TTO", name: "Trinidad and Tobago" },
        { key: "TUN", name: "Tunisia" },
        { key: "TUR", name: "Turkey" },
        { key: "TCA", name: "Turks and Caicos Islands" },
        { key: "ARE", name: "UAE" },
        { key: "UGA", name: "Uganda" },
        { key: "GBR", name: "UK" },
        { key: "UKR", name: "Ukraine" },
        { key: "URY", name: "Uruguay" },
        { key: "USA", name: "USA" },
        { key: "UZB", name: "Uzbekistan" },
        { key: "VEN", name: "Venezuela Bolivarian Republic of" },
        { key: "VNM", name: "Vietnam" },
        { key: "ZMB", name: "Zambia" },
        { key: "ZWE", name: "Zimbabwe" }
      ]
    };
  },
  methods: {
    OnSubmit(name, type) {
      if (type !== "reset") {
        if (name && name !== "") {
          this.$emit("get-country", name && name !== "" ? name : null);
          this.isSrchShow = false;
        } else {
          const reCntry = this.$refs["srchInput"].value;
          if (reCntry && reCntry !== "") {
            this.isSrchShow = false;
          }
          this.$emit("get-country", reCntry && reCntry !== "" ? reCntry : null);
        }
      } else {
        this.isSrchShow = true;
        this.$emit("get-country", null);
      }
      this.list = [];
    },
    cntryChng(e) {
      if (e) {
        this.list = this.countries.filter(ec =>
          ec.name.toLowerCase().includes(e.toLowerCase())
        );
      } else {
        this.list = [];
        this.info = undefined;
      }
    },
    itemClick(name) {
      this.list = [];
      this.OnSubmit(name);
    }
  }
};
</script>

<style>
.lviewChild {
  height: 35vh !important;
}
.listView {
  height: auto !important;
  max-height: 35vh !important;
  overflow-y: auto;
  position: absolute;
  z-index: 10;
  width: 90%;
  margin: 0 auto;
  border: 1px solid #c0c0c038;
  border-radius: 5px;
  -webkit-box-shadow: 0px 8px 10px 0px silver;
  box-shadow: 0px 8px 10px 0px silver;
  top: 69px;
}
.hvrItem:hover {
  background: silver;
}
.cstmBtn {
  min-width: 25% !important;
  max-width: 45% !important;
  height: 35px !important;
}
.cstmRow {
  display: flex !important;
  justify-content: center !important;
  align-items: center !important;
}
</style>
