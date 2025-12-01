# SEARCH HUB APP <!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Number to City App</title>
  <style>
    /* Minimalistic blue & white theme */
    body {
      font-family: Arial, sans-serif;
      background-color: #f0f4f8;
      color: #003366;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: flex-start;
      padding: 40px 20px;
      min-height: 100vh;
    }
    h1 {
      font-size: 2rem;
      margin-bottom: 30px;
    }
    input {
      padding: 10px 15px;
      font-size: 16px;
      border: 2px solid #003366;
      border-radius: 5px;
      margin-right: 10px;
      width: 180px;
    }
    button {
      padding: 10px 20px;
      font-size: 16px;
      border: none;
      border-radius: 5px;
      background-color: #003366;
      color: white;
      cursor: pointer;
      transition: background-color 0.3s;
    }
    button:hover {
      background-color: #0055a5;
    }
    h2 {
      margin-top: 30px;
      font-size: 1.5rem;
    }
    @media (max-width: 500px) {
      input {
        width: 140px;
        margin-bottom: 10px;
      }
      button {
        width: 100%;
      }
    }
  </style>
</head>
<body>
  <h1>Number to City App</h1>
  <div>
    <input type="number" id="numberInput" placeholder="Enter a number">
    <button onclick="showCity()">Submit</button>
  </div>
  <h2 id="answer">Answer: </h2>

  <script>
    const numberCityMap = {
      // Hyderabad
      500:"Hyderabad",501:"Hyderabad",502:"Hyderabad",503:"Hyderabad",504:"Hyderabad",
      505:"Hyderabad",506:"Hyderabad",507:"Hyderabad",508:"Hyderabad",509:"Hyderabad",518:"Hyderabad",

      // Anantapura
      515:"Anantapura",

      // Tirupati
      516:"Tirupati",517:"Tirupati",524:"Tirupati",

      // Vijayawada
      520:"Vijayawada",521:"Vijayawada",522:"Vijayawada",523:"Vijayawada",533:"Vijayawada",534:"Vijayawada",

      // Vishakapatna
      530:"Vishakapatna",531:"Vishakapatna",764:"Vishakapatna",

      // Chennai
      600:"Chennai",601:"Chennai",602:"Chennai",603:"Chennai",604:"Chennai",605:"Chennai",606:"Chennai",607:"Chennai",608:"Chennai",
      631:"Chennai",632:"Chennai",635:"Chennai",

      // Trichy
      609:"Trichy",610:"Trichy",611:"Trichy",612:"Trichy",613:"Trichy",614:"Trichy",615:"Trichy",616:"Trichy",617:"Trichy",618:"Trichy",
      619:"Trichy",620:"Trichy",621:"Trichy",622:"Trichy",639:"Trichy",

      // Madurai
      623:"Madurai",624:"Madurai",625:"Madurai",626:"Madurai",627:"Madurai",628:"Madurai",629:"Madurai",630:"Madurai",

      // Coimbatore
      638:"Coimbatore",641:"Coimbatore",642:"Coimbatore",643:"Coimbatore",678:"Coimbatore",

      // Kozidoke
      673:"Kozidoke",676:"Kozidoke",

      // Trishur
      679:"Trishur",680:"Trishur",

      // Kochi
      681:"Kochi",682:"Kochi",683:"Kochi",684:"Kochi",685:"Kochi",686:"Kochi",687:"Kochi",688:"Kochi",689:"Kochi",

      // Thiruvananthapuram
      690:"Thiruvananthapuram",691:"Thiruvananthapuram",692:"Thiruvananthapuram",693:"Thiruvananthapuram",694:"Thiruvananthapuram",695:"Thiruvananthapuram",

      // Mumbai
      400:"Mumbai",401:"Mumbai",402:"Mumbai",404:"Mumbai",405:"Mumbai",406:"Mumbai",407:"Mumbai",408:"Mumbai",409:"Mumbai",410:"Mumbai",

      // Morgan
      403:"Morgan",416:"Morgan",

      // Pune
      411:"Pune",412:"Pune",413:"Pune",414:"Pune",415:"Pune",

      // Chhatrapati Sambhaji Nagar
      431:"Chhatrapati Sambhaji Nagar",

      // Nagpur
      440:"Nagpur",441:"Nagpur",442:"Nagpur",443:"Nagpur",444:"Nagpur",445:"Nagpur",446:"Nagpur",447:"Nagpur",448:"Nagpur",449:"Nagpur",

      // Jaipur
      300:"Jaipur",301:"Jaipur",302:"Jaipur",303:"Jaipur",304:"Jaipur",324:"Jaipur",331:"Jaipur",332:"Jaipur",333:"Jaipur",335:"Jaipur",

      // Ajmer
      305:"Ajmer",306:"Ajmer",307:"Ajmer",308:"Ajmer",309:"Ajmer",310:"Ajmer",311:"Ajmer",312:"Ajmer",

      // Jodhpur
      334:"Jodhpur",341:"Jodhpur",342:"Jodhpur",343:"Jodhpur",344:"Jodhpur",345:"Jodhpur",

      // Rajkot
      360:"Rajkot",361:"Rajkot",362:"Rajkot",363:"Rajkot",

      // Ahmedabad
      364:"Ahemadabad",365:"Ahemadabad",366:"Ahemadabad",367:"Ahemadabad",368:"Ahemadabad",369:"Ahemadabad",
      370:"Ahemadabad",371:"Ahemadabad",372:"Ahemadabad",373:"Ahemadabad",374:"Ahemadabad",375:"Ahemadabad",
      376:"Ahemadabad",377:"Ahemadabad",378:"Ahemadabad",379:"Ahemadabad",380:"Ahemadabad",381:"Ahemadabad",382:"Ahemadabad",

      // Surat
      391:"Surat",392:"Surat",393:"Surat",394:"Surat",395:"Surat",396:"Surat",

      // Gorakhpur
      271:"Gorakhpur",272:"Gorakhpur",273:"Gorakhpur",274:"Gorakhpur",

      // Rudrapur
      262:"Rudrapur",263:"Rudrapur",

      // Dehradun
      246:"Dehradun",247:"Dehradun",248:"Dehradun",249:"Dehradun",

      // Prayagraj
      211:"Prayagraj",212:"Prayagraj",230:"Prayagraj",231:"Prayagraj",232:"Prayagraj",233:"Prayagraj",
      275:"Prayagraj",276:"Prayagraj",277:"Prayagraj",221:"Prayagraj",

      // Kanpur
      208:"Kanpur",209:"Kanpur",210:"Kanpur",

      // Bareilly
      207:"Bareilly",242:"Bareilly",243:"Bareilly",244:"Bareilly",

      // Agra
      202:"Agra",204:"Agra",205:"Agra",206:"Agra",281:"Agra",282:"Agra",283:"Agra",284:"Agra",285:"Agra",

      // Ghaziabad
      201:"Ghaziabad",203:"Ghaziabad",247:"Ghaziabad",250:"Ghaziabad",251:"Ghaziabad",

      // Delhi
      110:"Delhi",

      // Gurgaon
      121:"Gurgaon",122:"Gurgaon",123:"Gurgaon",

      // Rohtak
      124:"Rohtak",125:"Rohtak",126:"Rohtak",127:"Rohtak",131:"Rohtak",

      // Ambala
      132:"Ambala",133:"Ambala",134:"Ambala",135:"Ambala",136:"Ambala",137:"Ambala",
      173:"Ambala",174:"Ambala",175:"Ambala",

      // Chandigarh
      140:"Chandigarh",147:"Chandigarh",160:"Chandigarh",

      // Ludhiana
      141:"Ludhiana",142:"Ludhiana",151:"Ludhiana",152:"Ludhiana",158:"Ludhiana",146:"Ludhiana",

      // Jalandhar
      143:"Jalandhar",144:"Jalandhar",146:"Jalandhar",

      // Pathankot
      145:"Pathankot",176:"Pathankot",177:"Pathankot",

      // Parwano
      171:"Parwano",172:"Parwano",

      // Jammu
      180:"Jammu",181:"Jammu",182:"Jammu",183:"Jammu",184:"Jammu",185:"Jammu",
      186:"Jammu",187:"Jammu",188:"Jammu",189:"Jammu",

      // Srinagar
      190:"Srinagar",191:"Srinagar",192:"Srinagar",193:"Srinagar",

      // Leh
      194:"Leh",

      // Extra questions
      700:"Kolkata",701:"Kolkata",702:"Kolkata",703:"Kolkata",704:"Kolkata",705:"Kolkata",706:"Kolkata",707:"Kolkata",708:"Kolkata",709:"Kolkata",
      710:"Kolkata",711:"Kolkata",712:"Kolkata",713:"Kolkata",714:"Deogarh",715:"Deogarh",716:"Kolkata",717:"Kolkata",718:"Kolkata",719:"Kolkata",
      720:"Kolkata",721:"Kolkata",722:"Kolkata",723:"Kolkata",724:"Kolkata",725:"Kolkata",726:"Kolkata",727:"Kolkata",728:"Kolkata",729:"Kolkata",
      730:"Kolkata",731:"Kolkata",741:"Kolkata",742:"Kolkata",743:"Kolkata",

      732:"Siliguri",733:"Siliguri",734:"Siliguri",735:"Siliguri",736:"Siliguri",737:"Siliguri",
      751:"Bhuvaneshwar",752:"Bhuvaneshwar",753:"Bhuvaneshwar",754:"Bhuvaneshwar",755:"Bhuvaneshwar",756:"Bhuvaneshwar",757:"Bhuvaneshwar",758:"Bhuvaneshwar",759:"Bhuvaneshwar",
      760:"Berahampur",761:"Berahampur",762:"Berahampur",763:"Berahampur",765:"Berahampur",
      766:"Sambalpur",767:"Sambalpur",768:"Sambalpur",769:"Sambalpur",770:"Sambalpur",
      781:"Guwhati",782:"Guwhati",783:"Guwhati",784:"Guwhati",785:"Guwhati",786:"Dibrugarh",787:"Guwahati",788:"Silchar",789:"Guwahati",790:"Guwahati",
      791:"Itanagar",792:"Dibrugarh",793:"Shillong",794:"Shillong",795:"Imphal",796:"Aizwal",797:"Dimapur",798:"Dimapur",799:"Agartala",

      821:"Patna",822:"Ranchi",823:"Patna",824:"Patna",825:"Ranchi",826:"Ranchi",827:"Ranchi",828:"Ranchi",829:"Ranchi",
      831:"Jamshedpur",832:"Jamshedpur",833:"Jamshedpur",834:"Ranchi",835:"Ranchi",
      841:"Patna",842:"Muzaffarpur",843:"Muzaffarpur",844:"Patna",845:"Muzaffarpur",846:"Muzaffarpur",847:"Muzaffarpur",848:"Muzaffarpur",849:"Muzaffarpur",
      851:"Patna",852:"Patna",853:"Patna",854:"Patna",855:"Patna",856:"Patna",857:"Patna",858:"Patna",859:"Patna",
    };

    function showCity() {
      const num = document.getElementById("numberInput").value;
      const answer = numberCityMap[num];
      document.getElementById("answer").innerText = answer ? `Answer: ${answer}` : "No answer found for this number";
    }
  </script>
</body>
</html>
