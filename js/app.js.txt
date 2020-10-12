
async function abc(){
    const data = await fetch('https://api.covid19india.org/v4/data.json');
    const obj = await data.json();
    var x = obj.TT
    var total_case =  x.total.confirmed;
    var total_cured = x.total.recovered;
    var total_death = x.total.deceased;
    var total_d = document.getElementById("total_death")
    var total_c = document.getElementById("total_cases")
    var total_r = document.getElementById("total_cured")
    total_d.innerHTML = total_death;
    total_c.innerHTML = total_case;
    total_r.innerHTML = total_cured;

    statecode =
        {
        "AN":"Andaman and Nicobar Islands",
        "AP":"Andhra Pradesh",
        "AR":"Arunachal Pradesh",	
        "AS":"Assam",
        "BR":"Bihar",
        "CH":"Chandigarh",
        "CT":"Chhattisgarh",
        "DN":"Dadra and Nagar Haveli and Daman and Diu",
        "DL":"Delhi",
        "GA":"Goa",
        "GJ":"Gujarat",
        "HR":"Haryana",
        "HP":"Himachal Pradesh",
        "JK":"Jammu and Kashmir",
        "JH":"Jharkhand",
        "KA":"Karnataka",
        "KL":"Kerala",
        "LA":"Ladak",
        "MP":"Madhya Pradesh",
        "MH":"Maharashtra",
        "MN":"Manipur",
        "ML":"Meghalaya",
        "MZ":"Mizoram",	
        "NL":"Nagaland",
        "OR":"Odisha",
        "PY":"Puducherry",
        "PB":"Punjab",
        "RJ":"Rajasthan",
        "SK":"Sikkim",
        "TN":"Tamil Nadu",
        "TG":"Telangana",
        "TR":"Tripura",
        "UP":"Uttar Pradesh",
        "UT":"Uttarakhand",
        "WB":"West Bengal"
        };


    var state_data = document.getElementById("state_data");	
    for (const [key, value] of Object.entries(obj)) {
        if(key != "TT"){
            const tr = document.createElement('tr');
            const th_state = document.createElement('th');
            th_state.setAttribute('scope','row');
            th_state.textContent = statecode[key];
            const td_case = document.createElement('td');
            td_case.textContent = value.total.confirmed;
            const td_cured = document.createElement('td');
            td_cured.textContent = value.total.recovered;
            const td_death = document.createElement('td');
            td_death.textContent = value.total.deceased;
            const td_active = document.createElement('td');
            td_active.textContent = value.total.confirmed - value.total.recovered - value.total.deceased;

            state_data.appendChild(tr);
            tr.appendChild(th_state);
            tr.appendChild(td_case);
            tr.appendChild(td_active);
            tr.appendChild(td_cured);
            tr.appendChild(td_death);

    }

        }
        
    
}

abc();