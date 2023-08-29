# SQL Q&A

<br>

### these are the libraries used 

<br>

```python
!pip install sqlalchemy PyMySQL --quiet
!pip install pandas-profiling --quiet

```


```python
import sqlalchemy
from sqlalchemy import create_engine

```


```python
engine = create_engine('mysql+pymysql://username:password@host/database')

```


```python
%load_ext sql

```


```python
!pip install ipython-sql --quiet

```


```python
from getpass import getpass

password = getpass()
```

    ········



```python
conn_str = "mysql+pymysql://root:{}@localhost:3306/EV_schema".format(password)
```


```python
%sql {conn_str}
```
<br>

# The EV Cars Data 

<br>

```python
%sql SELECT * from evcars;
```





<table>
    <thead>
        <tr>
            <th>Brand</th>
            <th>Model</th>
            <th>AccelSec</th>
            <th>TopSpeed_KmH</th>
            <th>Range_Km</th>
            <th>Efficiency_WhKm</th>
            <th>FastCharge_KmH</th>
            <th>RapidCharge</th>
            <th>PowerTrain</th>
            <th>PlugType</th>
            <th>BodyStyle</th>
            <th>Segment</th>
            <th>Seats</th>
            <th>priceeuro</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Tesla </td>
            <td>Model 3 Long Range Dual Motor</td>
            <td>4.6</td>
            <td>233</td>
            <td>450</td>
            <td>161</td>
            <td>940</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>Sedan</td>
            <td>D</td>
            <td>5</td>
            <td>55480.00</td>
        </tr>
        <tr>
            <td>Volkswagen </td>
            <td>ID.3 Pure</td>
            <td>10.0</td>
            <td>160</td>
            <td>270</td>
            <td>167</td>
            <td>250</td>
            <td>Yes</td>
            <td>RWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>C</td>
            <td>5</td>
            <td>30000.00</td>
        </tr>
        <tr>
            <td>Polestar </td>
            <td>2</td>
            <td>4.7</td>
            <td>210</td>
            <td>400</td>
            <td>181</td>
            <td>620</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>Liftback</td>
            <td>D</td>
            <td>5</td>
            <td>56440.00</td>
        </tr>
        <tr>
            <td>BMW </td>
            <td>iX3 </td>
            <td>6.8</td>
            <td>180</td>
            <td>360</td>
            <td>206</td>
            <td>560</td>
            <td>Yes</td>
            <td>RWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>D</td>
            <td>5</td>
            <td>68040.00</td>
        </tr>
        <tr>
            <td>Honda </td>
            <td>e </td>
            <td>9.5</td>
            <td>145</td>
            <td>170</td>
            <td>168</td>
            <td>190</td>
            <td>Yes</td>
            <td>RWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>B</td>
            <td>4</td>
            <td>32997.00</td>
        </tr>
        <tr>
            <td>Lucid </td>
            <td>Air </td>
            <td>2.8</td>
            <td>250</td>
            <td>610</td>
            <td>180</td>
            <td>620</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>Sedan</td>
            <td>F</td>
            <td>5</td>
            <td>105000.00</td>
        </tr>
        <tr>
            <td>Volkswagen </td>
            <td>e-Golf </td>
            <td>9.6</td>
            <td>150</td>
            <td>190</td>
            <td>168</td>
            <td>220</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>C</td>
            <td>5</td>
            <td>31900.00</td>
        </tr>
        <tr>
            <td>Peugeot </td>
            <td>e-208 </td>
            <td>8.1</td>
            <td>150</td>
            <td>275</td>
            <td>164</td>
            <td>420</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>B</td>
            <td>5</td>
            <td>29682.00</td>
        </tr>
        <tr>
            <td>Tesla </td>
            <td>Model 3 Standard Range Plus</td>
            <td>5.6</td>
            <td>225</td>
            <td>310</td>
            <td>153</td>
            <td>650</td>
            <td>Yes</td>
            <td>RWD</td>
            <td>Type 2 CCS</td>
            <td>Sedan</td>
            <td>D</td>
            <td>5</td>
            <td>46380.00</td>
        </tr>
        <tr>
            <td>Audi </td>
            <td>Q4 e-tron </td>
            <td>6.3</td>
            <td>180</td>
            <td>400</td>
            <td>193</td>
            <td>540</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>D</td>
            <td>5</td>
            <td>55000.00</td>
        </tr>
        <tr>
            <td>Mercedes </td>
            <td>EQC 400 4MATIC</td>
            <td>5.1</td>
            <td>180</td>
            <td>370</td>
            <td>216</td>
            <td>440</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>D</td>
            <td>5</td>
            <td>69484.00</td>
        </tr>
        <tr>
            <td>Nissan </td>
            <td>Leaf </td>
            <td>7.9</td>
            <td>144</td>
            <td>220</td>
            <td>164</td>
            <td>230</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CHAdeMO</td>
            <td>Hatchback</td>
            <td>C</td>
            <td>5</td>
            <td>29234.00</td>
        </tr>
        <tr>
            <td>Hyundai </td>
            <td>Kona Electric 64 kWh</td>
            <td>7.9</td>
            <td>167</td>
            <td>400</td>
            <td>160</td>
            <td>380</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>B</td>
            <td>5</td>
            <td>40795.00</td>
        </tr>
        <tr>
            <td>BMW </td>
            <td>i4 </td>
            <td>4.0</td>
            <td>200</td>
            <td>450</td>
            <td>178</td>
            <td>650</td>
            <td>Yes</td>
            <td>RWD</td>
            <td>Type 2 CCS</td>
            <td>Sedan</td>
            <td>D</td>
            <td>5</td>
            <td>65000.00</td>
        </tr>
        <tr>
            <td>Hyundai </td>
            <td>IONIQ Electric</td>
            <td>9.7</td>
            <td>165</td>
            <td>250</td>
            <td>153</td>
            <td>210</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>Liftback</td>
            <td>C</td>
            <td>5</td>
            <td>34459.00</td>
        </tr>
        <tr>
            <td>Volkswagen </td>
            <td>ID.3 Pro S</td>
            <td>7.9</td>
            <td>160</td>
            <td>440</td>
            <td>175</td>
            <td>590</td>
            <td>Yes</td>
            <td>RWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>C</td>
            <td>4</td>
            <td>40936.00</td>
        </tr>
        <tr>
            <td>Porsche </td>
            <td>Taycan Turbo S</td>
            <td>2.8</td>
            <td>260</td>
            <td>375</td>
            <td>223</td>
            <td>780</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>Sedan</td>
            <td>F</td>
            <td>4</td>
            <td>180781.00</td>
        </tr>
        <tr>
            <td>Volkswagen </td>
            <td>e-Up! </td>
            <td>11.9</td>
            <td>130</td>
            <td>195</td>
            <td>166</td>
            <td>170</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>A</td>
            <td>4</td>
            <td>21421.00</td>
        </tr>
        <tr>
            <td>MG </td>
            <td>ZS EV</td>
            <td>8.2</td>
            <td>140</td>
            <td>220</td>
            <td>193</td>
            <td>260</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>B</td>
            <td>5</td>
            <td>30000.00</td>
        </tr>
        <tr>
            <td>Mini </td>
            <td>Cooper SE </td>
            <td>7.3</td>
            <td>150</td>
            <td>185</td>
            <td>156</td>
            <td>260</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>B</td>
            <td>4</td>
            <td>31681.00</td>
        </tr>
        <tr>
            <td>Opel </td>
            <td>Corsa-e </td>
            <td>8.1</td>
            <td>150</td>
            <td>275</td>
            <td>164</td>
            <td>420</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>B</td>
            <td>5</td>
            <td>29146.00</td>
        </tr>
        <tr>
            <td>Tesla </td>
            <td>Model Y Long Range Dual Motor</td>
            <td>5.1</td>
            <td>217</td>
            <td>425</td>
            <td>171</td>
            <td>930</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>D</td>
            <td>7</td>
            <td>58620.00</td>
        </tr>
        <tr>
            <td>Skoda </td>
            <td>Enyaq iV 50</td>
            <td>10.0</td>
            <td>160</td>
            <td>290</td>
            <td>179</td>
            <td>230</td>
            <td>Yes</td>
            <td>RWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>C</td>
            <td>5</td>
            <td>35000.00</td>
        </tr>
        <tr>
            <td>Audi </td>
            <td>e-tron GT </td>
            <td>3.5</td>
            <td>240</td>
            <td>425</td>
            <td>197</td>
            <td>850</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>Sedan</td>
            <td>F</td>
            <td>4</td>
            <td>125000.00</td>
        </tr>
        <tr>
            <td>Tesla </td>
            <td>Model 3 Long Range Performance</td>
            <td>3.4</td>
            <td>261</td>
            <td>435</td>
            <td>167</td>
            <td>910</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>Sedan</td>
            <td>D</td>
            <td>5</td>
            <td>61480.00</td>
        </tr>
        <tr>
            <td>Volkswagen </td>
            <td>ID.4 </td>
            <td>7.5</td>
            <td>160</td>
            <td>420</td>
            <td>183</td>
            <td>560</td>
            <td>Yes</td>
            <td>RWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>C</td>
            <td>5</td>
            <td>45000.00</td>
        </tr>
        <tr>
            <td>Volkswagen </td>
            <td>ID.3 Pro</td>
            <td>9.0</td>
            <td>160</td>
            <td>350</td>
            <td>166</td>
            <td>490</td>
            <td>Yes</td>
            <td>RWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>C</td>
            <td>5</td>
            <td>33000.00</td>
        </tr>
        <tr>
            <td>Volvo </td>
            <td>XC40 P8 AWD Recharge</td>
            <td>4.9</td>
            <td>180</td>
            <td>375</td>
            <td>200</td>
            <td>470</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>C</td>
            <td>5</td>
            <td>60437.00</td>
        </tr>
        <tr>
            <td>BMW </td>
            <td>i3 120 Ah</td>
            <td>7.3</td>
            <td>150</td>
            <td>235</td>
            <td>161</td>
            <td>270</td>
            <td>Yes</td>
            <td>RWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>B</td>
            <td>4</td>
            <td>38017.00</td>
        </tr>
        <tr>
            <td>Peugeot </td>
            <td>e-2008 SUV </td>
            <td>8.5</td>
            <td>150</td>
            <td>250</td>
            <td>180</td>
            <td>380</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>B</td>
            <td>5</td>
            <td>34361.00</td>
        </tr>
        <tr>
            <td>Audi </td>
            <td>e-tron 50 quattro</td>
            <td>6.8</td>
            <td>190</td>
            <td>280</td>
            <td>231</td>
            <td>450</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>E</td>
            <td>5</td>
            <td>67358.00</td>
        </tr>
        <tr>
            <td>Kia </td>
            <td>e-Niro 64 kWh</td>
            <td>7.8</td>
            <td>167</td>
            <td>370</td>
            <td>173</td>
            <td>350</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>C</td>
            <td>5</td>
            <td>38105.00</td>
        </tr>
        <tr>
            <td>Renault </td>
            <td>Zoe ZE50 R110</td>
            <td>11.4</td>
            <td>135</td>
            <td>315</td>
            <td>165</td>
            <td>230</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>B</td>
            <td>5</td>
            <td>31184.00</td>
        </tr>
        <tr>
            <td>Tesla </td>
            <td>Cybertruck Tri Motor</td>
            <td>3.0</td>
            <td>210</td>
            <td>750</td>
            <td>267</td>
            <td>710</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>Pickup</td>
            <td>N</td>
            <td>6</td>
            <td>75000.00</td>
        </tr>
        <tr>
            <td>Mazda </td>
            <td>MX-30 </td>
            <td>9.0</td>
            <td>150</td>
            <td>180</td>
            <td>178</td>
            <td>240</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>C</td>
            <td>5</td>
            <td>32646.00</td>
        </tr>
        <tr>
            <td>Nissan </td>
            <td>Leaf e+</td>
            <td>7.3</td>
            <td>157</td>
            <td>325</td>
            <td>172</td>
            <td>390</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CHAdeMO</td>
            <td>Hatchback</td>
            <td>C</td>
            <td>5</td>
            <td>37237.00</td>
        </tr>
        <tr>
            <td>Lexus </td>
            <td>UX 300e</td>
            <td>7.5</td>
            <td>160</td>
            <td>270</td>
            <td>193</td>
            <td>190</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CHAdeMO</td>
            <td>SUV</td>
            <td>C</td>
            <td>5</td>
            <td>50000.00</td>
        </tr>
        <tr>
            <td>CUPRA </td>
            <td>el-Born </td>
            <td>6.5</td>
            <td>160</td>
            <td>425</td>
            <td>181</td>
            <td>570</td>
            <td>Yes</td>
            <td>RWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>C</td>
            <td>4</td>
            <td>45000.00</td>
        </tr>
        <tr>
            <td>Renault </td>
            <td>Zoe ZE50 R135</td>
            <td>9.5</td>
            <td>140</td>
            <td>310</td>
            <td>168</td>
            <td>230</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>B</td>
            <td>5</td>
            <td>33133.00</td>
        </tr>
        <tr>
            <td>Mercedes </td>
            <td>EQA </td>
            <td>5.0</td>
            <td>200</td>
            <td>350</td>
            <td>171</td>
            <td>440</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>C</td>
            <td>5</td>
            <td>45000.00</td>
        </tr>
        <tr>
            <td>Tesla </td>
            <td>Model S Long Range</td>
            <td>3.8</td>
            <td>250</td>
            <td>515</td>
            <td>184</td>
            <td>560</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2</td>
            <td>Liftback</td>
            <td>F</td>
            <td>5</td>
            <td>79990.00</td>
        </tr>
        <tr>
            <td>Hyundai </td>
            <td>Kona Electric 39 kWh</td>
            <td>9.9</td>
            <td>155</td>
            <td>255</td>
            <td>154</td>
            <td>210</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>B</td>
            <td>5</td>
            <td>33971.00</td>
        </tr>
        <tr>
            <td>Audi </td>
            <td>e-tron Sportback 55 quattro</td>
            <td>5.7</td>
            <td>200</td>
            <td>380</td>
            <td>228</td>
            <td>610</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>E</td>
            <td>5</td>
            <td>81639.00</td>
        </tr>
        <tr>
            <td>Skoda </td>
            <td>CITIGOe iV </td>
            <td>12.3</td>
            <td>130</td>
            <td>195</td>
            <td>166</td>
            <td>170</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>A</td>
            <td>4</td>
            <td>24534.00</td>
        </tr>
        <tr>
            <td>SEAT </td>
            <td>Mii Electric </td>
            <td>12.3</td>
            <td>130</td>
            <td>195</td>
            <td>166</td>
            <td>170</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>A</td>
            <td>4</td>
            <td>20129.00</td>
        </tr>
        <tr>
            <td>Kia </td>
            <td>e-Soul 64 kWh</td>
            <td>7.9</td>
            <td>167</td>
            <td>365</td>
            <td>175</td>
            <td>340</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>B</td>
            <td>5</td>
            <td>36837.00</td>
        </tr>
        <tr>
            <td>Opel </td>
            <td>Ampera-e </td>
            <td>7.3</td>
            <td>150</td>
            <td>335</td>
            <td>173</td>
            <td>210</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>MPV</td>
            <td>B</td>
            <td>5</td>
            <td>41906.00</td>
        </tr>
        <tr>
            <td>Porsche </td>
            <td>Taycan 4S</td>
            <td>4.0</td>
            <td>250</td>
            <td>365</td>
            <td>195</td>
            <td>730</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>Sedan</td>
            <td>F</td>
            <td>4</td>
            <td>102945.00</td>
        </tr>
        <tr>
            <td>Lightyear </td>
            <td>One </td>
            <td>10.0</td>
            <td>150</td>
            <td>575</td>
            <td>104</td>
            <td>540</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>Liftback</td>
            <td>F</td>
            <td>5</td>
            <td>149000.00</td>
        </tr>
        <tr>
            <td>Aiways </td>
            <td>U5 </td>
            <td>9.0</td>
            <td>150</td>
            <td>335</td>
            <td>188</td>
            <td>350</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>C</td>
            <td>5</td>
            <td>36057.00</td>
        </tr>
        <tr>
            <td>Audi </td>
            <td>e-tron 55 quattro</td>
            <td>5.7</td>
            <td>200</td>
            <td>365</td>
            <td>237</td>
            <td>590</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>E</td>
            <td>5</td>
            <td>79445.00</td>
        </tr>
        <tr>
            <td>Tesla </td>
            <td>Roadster </td>
            <td>2.1</td>
            <td>410</td>
            <td>970</td>
            <td>206</td>
            <td>920</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>Cabrio</td>
            <td>S</td>
            <td>4</td>
            <td>215000.00</td>
        </tr>
        <tr>
            <td>Opel </td>
            <td>Mokka-e </td>
            <td>8.5</td>
            <td>150</td>
            <td>255</td>
            <td>176</td>
            <td>390</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>B</td>
            <td>5</td>
            <td>35000.00</td>
        </tr>
        <tr>
            <td>Skoda </td>
            <td>Enyaq iV 80</td>
            <td>8.8</td>
            <td>160</td>
            <td>420</td>
            <td>183</td>
            <td>560</td>
            <td>Yes</td>
            <td>RWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>C</td>
            <td>5</td>
            <td>40000.00</td>
        </tr>
        <tr>
            <td>Tesla </td>
            <td>Model X Long Range</td>
            <td>4.6</td>
            <td>250</td>
            <td>450</td>
            <td>211</td>
            <td>490</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2</td>
            <td>SUV</td>
            <td>F</td>
            <td>7</td>
            <td>85990.00</td>
        </tr>
        <tr>
            <td>Honda </td>
            <td>e Advance</td>
            <td>8.3</td>
            <td>145</td>
            <td>170</td>
            <td>168</td>
            <td>190</td>
            <td>Yes</td>
            <td>RWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>B</td>
            <td>4</td>
            <td>35921.00</td>
        </tr>
        <tr>
            <td>DS </td>
            <td>3 Crossback E-Tense</td>
            <td>8.7</td>
            <td>150</td>
            <td>250</td>
            <td>180</td>
            <td>380</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>B</td>
            <td>5</td>
            <td>37422.00</td>
        </tr>
        <tr>
            <td>Citroen </td>
            <td>e-C4 </td>
            <td>9.7</td>
            <td>150</td>
            <td>250</td>
            <td>180</td>
            <td>380</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>C</td>
            <td>5</td>
            <td>40000.00</td>
        </tr>
        <tr>
            <td>Tesla </td>
            <td>Model S Performance</td>
            <td>2.5</td>
            <td>261</td>
            <td>505</td>
            <td>188</td>
            <td>550</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2</td>
            <td>Liftback</td>
            <td>F</td>
            <td>5</td>
            <td>96990.00</td>
        </tr>
        <tr>
            <td>Renault </td>
            <td>Zoe ZE40 R110</td>
            <td>11.4</td>
            <td>135</td>
            <td>255</td>
            <td>161</td>
            <td>230</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>B</td>
            <td>5</td>
            <td>29234.00</td>
        </tr>
        <tr>
            <td>Tesla </td>
            <td>Model Y Long Range Performance</td>
            <td>3.7</td>
            <td>241</td>
            <td>410</td>
            <td>177</td>
            <td>900</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>D</td>
            <td>7</td>
            <td>65620.00</td>
        </tr>
        <tr>
            <td>Nissan </td>
            <td>Ariya 87kWh</td>
            <td>7.6</td>
            <td>160</td>
            <td>440</td>
            <td>198</td>
            <td>520</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>C</td>
            <td>5</td>
            <td>50000.00</td>
        </tr>
        <tr>
            <td>Jaguar </td>
            <td>I-Pace </td>
            <td>4.8</td>
            <td>200</td>
            <td>365</td>
            <td>232</td>
            <td>340</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>E</td>
            <td>5</td>
            <td>75351.00</td>
        </tr>
        <tr>
            <td>Ford </td>
            <td>Mustang Mach-E ER RWD</td>
            <td>7.0</td>
            <td>180</td>
            <td>450</td>
            <td>200</td>
            <td>430</td>
            <td>Yes</td>
            <td>RWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>D</td>
            <td>5</td>
            <td>54475.00</td>
        </tr>
        <tr>
            <td>Porsche </td>
            <td>Taycan 4S Plus</td>
            <td>4.0</td>
            <td>250</td>
            <td>425</td>
            <td>197</td>
            <td>890</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>Sedan</td>
            <td>F</td>
            <td>4</td>
            <td>109302.00</td>
        </tr>
        <tr>
            <td>Nissan </td>
            <td>e-NV200 Evalia </td>
            <td>14.0</td>
            <td>123</td>
            <td>190</td>
            <td>200</td>
            <td>190</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 1 CHAdeMO</td>
            <td>SPV</td>
            <td>N</td>
            <td>7</td>
            <td>33246.00</td>
        </tr>
        <tr>
            <td>Tesla </td>
            <td>Cybertruck Dual Motor</td>
            <td>5.0</td>
            <td>190</td>
            <td>460</td>
            <td>261</td>
            <td>710</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>Pickup</td>
            <td>N</td>
            <td>6</td>
            <td>55000.00</td>
        </tr>
        <tr>
            <td>Ford </td>
            <td>Mustang Mach-E ER AWD</td>
            <td>6.0</td>
            <td>180</td>
            <td>430</td>
            <td>209</td>
            <td>410</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>D</td>
            <td>5</td>
            <td>62900.00</td>
        </tr>
        <tr>
            <td>BMW </td>
            <td>i3s 120 Ah</td>
            <td>6.9</td>
            <td>160</td>
            <td>230</td>
            <td>165</td>
            <td>260</td>
            <td>Yes</td>
            <td>RWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>B</td>
            <td>4</td>
            <td>41526.00</td>
        </tr>
        <tr>
            <td>Skoda </td>
            <td>Enyaq iV 80X</td>
            <td>7.0</td>
            <td>160</td>
            <td>400</td>
            <td>193</td>
            <td>540</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>C</td>
            <td>5</td>
            <td>45000.00</td>
        </tr>
        <tr>
            <td>Porsche </td>
            <td>Taycan Cross Turismo </td>
            <td>3.5</td>
            <td>250</td>
            <td>385</td>
            <td>217</td>
            <td>770</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>Station</td>
            <td>F</td>
            <td>4</td>
            <td>150000.00</td>
        </tr>
        <tr>
            <td>Byton </td>
            <td>M-Byte 95 kWh 4WD</td>
            <td>5.5</td>
            <td>190</td>
            <td>390</td>
            <td>244</td>
            <td>460</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>E</td>
            <td>5</td>
            <td>64000.00</td>
        </tr>
        <tr>
            <td>Sono </td>
            <td>Sion </td>
            <td>9.0</td>
            <td>140</td>
            <td>225</td>
            <td>156</td>
            <td>270</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>C</td>
            <td>5</td>
            <td>25500.00</td>
        </tr>
        <tr>
            <td>Kia </td>
            <td>e-Niro 39 kWh</td>
            <td>9.8</td>
            <td>155</td>
            <td>235</td>
            <td>167</td>
            <td>230</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>C</td>
            <td>5</td>
            <td>34400.00</td>
        </tr>
        <tr>
            <td>Audi </td>
            <td>Q4 Sportback e-tron </td>
            <td>6.3</td>
            <td>180</td>
            <td>410</td>
            <td>188</td>
            <td>550</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>D</td>
            <td>5</td>
            <td>57500.00</td>
        </tr>
        <tr>
            <td>Ford </td>
            <td>Mustang Mach-E SR AWD</td>
            <td>6.0</td>
            <td>180</td>
            <td>340</td>
            <td>206</td>
            <td>360</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>D</td>
            <td>5</td>
            <td>54000.00</td>
        </tr>
        <tr>
            <td>Porsche </td>
            <td>Taycan Turbo</td>
            <td>3.2</td>
            <td>260</td>
            <td>390</td>
            <td>215</td>
            <td>810</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>Sedan</td>
            <td>F</td>
            <td>4</td>
            <td>148301.00</td>
        </tr>
        <tr>
            <td>Volkswagen </td>
            <td>ID.3 1st</td>
            <td>7.3</td>
            <td>160</td>
            <td>340</td>
            <td>171</td>
            <td>470</td>
            <td>Yes</td>
            <td>RWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>C</td>
            <td>5</td>
            <td>38987.00</td>
        </tr>
        <tr>
            <td>Tesla </td>
            <td>Model X Performance</td>
            <td>2.8</td>
            <td>250</td>
            <td>440</td>
            <td>216</td>
            <td>480</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2</td>
            <td>SUV</td>
            <td>F</td>
            <td>7</td>
            <td>102990.00</td>
        </tr>
        <tr>
            <td>Ford </td>
            <td>Mustang Mach-E SR RWD</td>
            <td>6.6</td>
            <td>180</td>
            <td>360</td>
            <td>194</td>
            <td>380</td>
            <td>Yes</td>
            <td>RWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>D</td>
            <td>5</td>
            <td>46900.00</td>
        </tr>
        <tr>
            <td>Mercedes </td>
            <td>EQV 300 Long</td>
            <td>10.0</td>
            <td>140</td>
            <td>330</td>
            <td>273</td>
            <td>290</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>SPV</td>
            <td>N</td>
            <td>7</td>
            <td>70631.00</td>
        </tr>
        <tr>
            <td>Fiat </td>
            <td>500e Hatchback</td>
            <td>9.0</td>
            <td>150</td>
            <td>250</td>
            <td>168</td>
            <td>330</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>B</td>
            <td>4</td>
            <td>34900.00</td>
        </tr>
        <tr>
            <td>Tesla </td>
            <td>Cybertruck Single Motor</td>
            <td>7.0</td>
            <td>180</td>
            <td>390</td>
            <td>256</td>
            <td>740</td>
            <td>Yes</td>
            <td>RWD</td>
            <td>Type 2 CCS</td>
            <td>Pickup</td>
            <td>N</td>
            <td>6</td>
            <td>45000.00</td>
        </tr>
        <tr>
            <td>Audi </td>
            <td>e-tron Sportback 50 quattro</td>
            <td>6.8</td>
            <td>190</td>
            <td>295</td>
            <td>219</td>
            <td>470</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>E</td>
            <td>5</td>
            <td>69551.00</td>
        </tr>
        <tr>
            <td>Skoda </td>
            <td>Enyaq iV vRS</td>
            <td>6.2</td>
            <td>180</td>
            <td>400</td>
            <td>193</td>
            <td>540</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>C</td>
            <td>5</td>
            <td>47500.00</td>
        </tr>
        <tr>
            <td>Skoda </td>
            <td>Enyaq iV 60</td>
            <td>9.0</td>
            <td>160</td>
            <td>320</td>
            <td>181</td>
            <td>440</td>
            <td>Yes</td>
            <td>RWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>C</td>
            <td>5</td>
            <td>37500.00</td>
        </tr>
        <tr>
            <td>Audi </td>
            <td>e-tron S 55 quattro</td>
            <td>4.5</td>
            <td>210</td>
            <td>320</td>
            <td>270</td>
            <td>510</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>E</td>
            <td>5</td>
            <td>93800.00</td>
        </tr>
        <tr>
            <td>Kia </td>
            <td>e-Soul 64 kWh</td>
            <td>7.9</td>
            <td>167</td>
            <td>365</td>
            <td>175</td>
            <td>320</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>B</td>
            <td>5</td>
            <td>36837.00</td>
        </tr>
        <tr>
            <td>Nissan </td>
            <td>Ariya e-4ORCE 87kWh</td>
            <td>5.7</td>
            <td>200</td>
            <td>420</td>
            <td>207</td>
            <td>500</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>C</td>
            <td>5</td>
            <td>57500.00</td>
        </tr>
        <tr>
            <td>Fiat </td>
            <td>500e Convertible</td>
            <td>9.0</td>
            <td>150</td>
            <td>250</td>
            <td>168</td>
            <td>330</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>Cabrio</td>
            <td>B</td>
            <td>4</td>
            <td>37900.00</td>
        </tr>
        <tr>
            <td>Volkswagen </td>
            <td>ID.3 Pro Performance</td>
            <td>7.3</td>
            <td>160</td>
            <td>340</td>
            <td>171</td>
            <td>470</td>
            <td>Yes</td>
            <td>RWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>C</td>
            <td>5</td>
            <td>35575.00</td>
        </tr>
        <tr>
            <td>Kia </td>
            <td>e-Soul 39 kWh</td>
            <td>9.9</td>
            <td>157</td>
            <td>230</td>
            <td>170</td>
            <td>220</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>B</td>
            <td>5</td>
            <td>33133.00</td>
        </tr>
        <tr>
            <td>Byton </td>
            <td>M-Byte 72 kWh 2WD</td>
            <td>7.5</td>
            <td>190</td>
            <td>325</td>
            <td>222</td>
            <td>420</td>
            <td>Yes</td>
            <td>RWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>E</td>
            <td>5</td>
            <td>53500.00</td>
        </tr>
        <tr>
            <td>Nissan </td>
            <td>Ariya 63kWh</td>
            <td>7.5</td>
            <td>160</td>
            <td>330</td>
            <td>191</td>
            <td>440</td>
            <td>Yes</td>
            <td>FWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>C</td>
            <td>5</td>
            <td>45000.00</td>
        </tr>
        <tr>
            <td>Audi </td>
            <td>e-tron S Sportback 55 quattro</td>
            <td>4.5</td>
            <td>210</td>
            <td>335</td>
            <td>258</td>
            <td>540</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>E</td>
            <td>5</td>
            <td>96050.00</td>
        </tr>
        <tr>
            <td>Nissan </td>
            <td>Ariya e-4ORCE 63kWh</td>
            <td>5.9</td>
            <td>200</td>
            <td>325</td>
            <td>194</td>
            <td>440</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>C</td>
            <td>5</td>
            <td>50000.00</td>
        </tr>
        <tr>
            <td>Nissan </td>
            <td>Ariya e-4ORCE 87kWh Performance</td>
            <td>5.1</td>
            <td>200</td>
            <td>375</td>
            <td>232</td>
            <td>450</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>Hatchback</td>
            <td>C</td>
            <td>5</td>
            <td>65000.00</td>
        </tr>
        <tr>
            <td>Byton </td>
            <td>M-Byte 95 kWh 2WD</td>
            <td>7.5</td>
            <td>190</td>
            <td>400</td>
            <td>238</td>
            <td>480</td>
            <td>Yes</td>
            <td>AWD</td>
            <td>Type 2 CCS</td>
            <td>SUV</td>
            <td>E</td>
            <td>5</td>
            <td>62000.00</td>
        </tr>
    </tbody>
</table>

<br>
<br>

## Question 1: How many car models are included in the dataset?


```sql
%%sql 
select count(distinct model) as TotalModel from evcars;

```

     





<table>
    <thead>
        <tr>
            <th>TotalModel</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>97</td>
        </tr>
    </tbody>
</table>


<br>
<br>


## Question 2: What is the average top speed of all the cars in the dataset?


```sql
%%sql
select avg(TopSpeed_Kmh) as AVG_topSpeed from evcars;
```

     





<table>
    <thead>
        <tr>
            <th>AVG_topSpeed</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>181.6531</td>
        </tr>
    </tbody>
</table>


<br>
<br>


## Question 3: Which car has the highest acceleration time (AccelSec)?


```sql
%%sql 
select brand, model, Accelsec from evcars order by AccelSec asc Limit 1;
```






<table>
    <thead>
        <tr>
            <th>brand</th>
            <th>model</th>
            <th>Accelsec</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Tesla </td>
            <td>Roadster </td>
            <td>2.1</td>
        </tr>
    </tbody>
</table>


<br>
<br>


## Question 4: What is the total range (Range_Km) covered by all SUVs?


```sql
%%sql 
select sum(range_km) as TotalRange_SUV from evcars Where Bodystyle = 'SUV';
```

     





<table>
    <thead>
        <tr>
            <th>TotalRange_SUV</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>15505</td>
        </tr>
    </tbody>
</table>


<br>
<br>


## Question 5: How many cars have a rapid charging option (RapidCharge = 'Yes')?


```sql
%%sql 
select count(*) as TotalRapidChargeCars from evcars Where RapidCharge = 'Yes';
```

    





<table>
    <thead>
        <tr>
            <th>TotalRapidChargeCars</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>98</td>
        </tr>
    </tbody>
</table>


<br>
<br>


## Question 6: What is the average price of cars in each segment (Segment column)?


```sql
%%sql 
select segment, Avg(priceeuro) as AvgPrive from evcars Group by Segment;  
```

     





<table>
    <thead>
        <tr>
            <th>segment</th>
            <th>AvgPrive</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>D</td>
            <td>58487.933333</td>
        </tr>
        <tr>
            <td>C</td>
            <td>41199.100000</td>
        </tr>
        <tr>
            <td>B</td>
            <td>34799.227273</td>
        </tr>
        <tr>
            <td>F</td>
            <td>119690.750000</td>
        </tr>
        <tr>
            <td>A</td>
            <td>22028.000000</td>
        </tr>
        <tr>
            <td>E</td>
            <td>74269.400000</td>
        </tr>
        <tr>
            <td>N</td>
            <td>55775.400000</td>
        </tr>
        <tr>
            <td>S</td>
            <td>215000.000000</td>
        </tr>
    </tbody>
</table>


<br>
<br>


## Question 7: What is the most common powertrain type (PowerTrain column)?


```sql
%%sql 
select powertrain, Count(*) as Powertraincount 
from evcars group by powertrain 
order by Powertraincount 
desc limit 1;  
```

     





<table>
    <thead>
        <tr>
            <th>powertrain</th>
            <th>Powertraincount</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>AWD</td>
            <td>41</td>
        </tr>
    </tbody>
</table>


<br>
<br>


## Question 8: How many cars have a range greater than 300 km and are priced under 40000 Euros?


```sql
%%sql 
select count(*) as Totalcar 
from evcars where range_km > 300 
AND Priceeuro < 40000;
```

    





<table>
    <thead>
        <tr>
            <th>Totalcar</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>11</td>
        </tr>
    </tbody>
</table>

<br>
<br>



## Question 9: What is the average efficiency (Efficiency_WhKm) of cars in each body style?


```sql
%%sql
select bodystyle, avg(Efficiency_WhKm) 
as AvgEfficiency 
from evcars group by Bodystyle;
```

    





<table>
    <thead>
        <tr>
            <th>bodystyle</th>
            <th>AvgEfficiency</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Sedan</td>
            <td>186.6000</td>
        </tr>
        <tr>
            <td>Hatchback</td>
            <td>173.0690</td>
        </tr>
        <tr>
            <td>Liftback</td>
            <td>162.0000</td>
        </tr>
        <tr>
            <td>SUV</td>
            <td>197.5778</td>
        </tr>
        <tr>
            <td>Pickup</td>
            <td>261.3333</td>
        </tr>
        <tr>
            <td>MPV</td>
            <td>173.0000</td>
        </tr>
        <tr>
            <td>Cabrio</td>
            <td>187.0000</td>
        </tr>
        <tr>
            <td>SPV</td>
            <td>236.5000</td>
        </tr>
        <tr>
            <td>Station</td>
            <td>217.0000</td>
        </tr>
    </tbody>
</table>
<br>
<br>

## Question 10: Which plug type (PlugType column) is associated with the highest number of cars?


```sql
%%sql 
select plugType, Count(*) as PlugTypeCount 
from evcars group by plugType 
order by plugtypecount 
desc LIMIT 1;
```

    





<table>
    <thead>
        <tr>
            <th>plugType</th>
            <th>PlugTypeCount</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Type 2 CCS</td>
            <td>90</td>
        </tr>
    </tbody>
</table>


