|	Key			|	R/W			|	Type							|	Category		|	Description																			|
|	----------	|	----------	|	----------------------------	|	-------------	|	----------------------------------------------------------------------------------- |
|	acp	|	R/W	|	bool	|	Config	|	allowChargePause	|
|	acs	|	R/W	|	uint8_t	|	Config	|	access_control user setting (Open=0, Wait=1, EVCMS=2)	|
|	acu	|	R	|	optional<int32_t>	|	Status	|	How many ampere is the car allowed to charge now?	|
|	adi	|	R	|	bool	|	Status	|	Is the 16A adapter used? Limits the current to 16A	|
|	alw	|	R	|	bool	|	Status	|	Is the car allowed to charge at all now?	|
|	alwt	|	R	|	int64_t	|	Status	|	timestamp of last alw change (use rbt to find out how long its ago)	|
|	ama	|	R/W	|	uint8_t	|	Config	|	ampere_max limit	|
|	amp	|	R/W	|	uint8_t	|	Config	|	requestedCurrent, used for display on LED ring and logic calculations	|
|	amt	|	R	|	int32_t	|	Status	|	temperatureCurrentLimit	|
|	ara	|	R/W	|	bool	|	Config	|	automatic stop remain in aWATTar	|
|	ate	|	R/W	|	double	|	Config	|	nextTripEnergy in Wh	|
|	atp	|	R	|	legacy	|	Status	|	nextTripPlanData	|
|	att	|	R/W	|	int32_t	|	Config	|	automatic stop time in seconds since day begin, calculation: (hours*3600)+(min	utes*60)+(seconds) |
|	aus	|	R	|	bool	|	Config	|	is australia	|
|	avgfhz	|	R	|	optional<float>	|	Status	|	Stromnetz average frequency (~50Hz)	|
|	awc	|	R/W	|	uint16_t	|	Config	|	awattar country (Austria=0, Germany=1,...)	|
|	awcp	|	R	|	legacy	|	Status	|	awattar current price	|
|	awe	|	R/W	|	bool	|	Config	|	useAwattar	|
|	awp	|	R/W	|	float	|	Config	|	awattarMaxPrice in ct	|
|	awpl	|	W	|	get: legacy set: JsonObject	|	Status	|	awattar price list (v2), timestamps are measured in unix-time, seconds since 1	970   |
|	c0e	|	R/W	|	uint64_t	|	Config	|	0. rfid cards energy	|
|	c0i	|	R/W	|	get: bool set: string	|	Config	|	0. rfid cards id	|
|	c0n	|	R/W	|	string	|	Config	|	0. rfid cards name	|
|	c1e	|	R/W	|	uint64_t	|	Config	|	1. rfid cards energy	|
|	c1i	|	R/W	|	get: bool set: string	|	Config	|	1. rfid cards id	|
|	c1n	|	R/W	|	string	|	Config	|	1. rfid cards name	|
|	c2e	|	R/W	|	uint64_t	|	Config	|	2. rfid cards energy	|
|	c2i	|	R/W	|	get: bool set: string	|	Config	|	2. rfid cards id	|
|	c2n	|	R/W	|	string	|	Config	|	2. rfid cards name	|
|	c3e	|	R/W	|	uint64_t	|	Config	|	3. rfid cards energy	|
|	c3i	|	R/W	|	get: bool set: string	|	Config	|	3. rfid cards id	|
|	c3n	|	R/W	|	string	|	Config	|	3. rfid cards name	|
|	c4e	|	R/W	|	uint64_t	|	Config	|	4. rfid cards energy	|
|	c4i	|	R/W	|	get: bool set: string	|	Config	|	4. rfid cards id	|
|	c4n	|	R/W	|	string	|	Config	|	4. rfid cards name	|
|	c5e	|	R/W	|	uint64_t	|	Config	|	5. rfid cards energy	|
|	c5i	|	R/W	|	get: bool set: string	|	Config	|	5. rfid cards id	|
|	c5n	|	R/W	|	string	|	Config	|	5. rfid cards name	|
|	c6e	|	R/W	|	uint64_t	|	Config	|	6. rfid cards energy	|
|	c6i	|	R/W	|	get: bool set: string	|	Config	|	6. rfid cards id	|
|	c6n	|	R/W	|	string	|	Config	|	6. rfid cards name	|
|	c7e	|	R/W	|	uint64_t	|	Config	|	7. rfid cards energy	|
|	c7i	|	R/W	|	get: bool set: string	|	Config	|	7. rfid cards id	|
|	c7n	|	R/W	|	string	|	Config	|	7. rfid cards name	|
|	c8e	|	R/W	|	uint64_t	|	Config	|	8. rfid cards energy	|
|	c8i	|	R/W	|	get: bool set: string	|	Config	|	8. rfid cards id	|
|	c8n	|	R/W	|	string	|	Config	|	8. rfid cards name	|
|	c9e	|	R/W	|	uint64_t	|	Config	|	9. rfid cards energy	|
|	c9i	|	R/W	|	get: bool set: string	|	Config	|	9. rfid cards id	|
|	c9n	|	R/W	|	string	|	Config	|	9. rfid cards name	|
|	car	|	R	|	optional<uint8_t>	|	Status	|	charge ctrl car state, null if no connection to chargectrl established (Unknow	n/Error=0, Idle=1, Charging=2, WaitCar=3, Complete=4, Error=5) |
|	cards	|	R/W	|	get: legacy set: JsonArray	|	Config	|	RFID cards array of objects, if you only want to change the second entry, send	an array with 1 empty and 1 filled card config object: [{}, {"name":"","energy":"","rfid":""}] |
|	ccd	|	R	|	legacy	|	Status	|	Connected controller data	|
|	cce	|	R	|	legacy	|	Status	|	Currently connected Ethernet	|
|	cch	|	R/W	|	string	|	Config	|	color_charging, format: #RRGGBB	|
|	cco	|	R/W	|	double	|	Config	|	car consumption (for app)	|
|	ccw	|	R	|	legacy	|	Status	|	Currently connected WiFi	|
|	cdi	|	R	|	legacy	|	Status	|	charging duration info (null=no charging in progress, type=0 counter going up,	type=1 duration in ms) |
|	cert	|	R	|	uint8_t	|	Config	|	Certification Status (0=NoCertification, 1=MidOnly, 2=MidEichrecht)	|
|	cfi	|	R/W	|	string	|	Config	|	color_finished, format: #RRGGBB	|
|	cid	|	R/W	|	string	|	Config	|	color_idle, format: #RRGGBB	|
|	cle	|	R	|	optional<string>	|	Status	|	Cloud last error	|
|	clea	|	R	|	optional<int64_t>	|	Status	|	Cloud last error (age)	|
|	cll	|	R	|	legacy	|	Status	|	Current limits list	|
|	clp	|	R/W	|	get: legacy set: JsonArray	|	Config	|	current limit presets, max. 5 entries	|
|	cmmr	|	R	|	uint16_t	|	Config	|	controllerMdnsMaxResults	|
|	cmp	|	R	|	string	|	Config	|	controllerMdnsProto	|
|	cms	|	R	|	string	|	Config	|	controllerMdnsService	|
|	cmse	|	R	|	bool	|	Config	|	controllerMdnsScanEnabled, set to false to completely disable any MDNS searche	s (debugging) |
|	csa	|	R	|	bool	|	Status	|	controller scan active (set to true to start scan)	|
|	csd	|	R/W	|	bool	|	Config	|	clear surplus data after break	|
|	ct	|	R/W	|	string	|	Config	|	car type, free text string (max. 64 characters)	|
|	ctrls	|	R	|	legacy	|	Status	|	Controllers search result	|
|	cwc	|	R/W	|	string	|	Config	|	color_waitcar, format: #RRGGBB	|
|	cwe	|	R/W	|	bool	|	Config	|	cloud websocket enabled	|
|	data	|	R	|	string	|	Status	|	grafana token from cloud for app	|
|	del	|	W	|	uint8_t	|	Unknown	|	set this to 0-9 to clear card (erases card name, energy and rfid id)	|
|	deltaa	|	R	|	float	|	Unknown	|	deltaA	|
|	deltap	|	R	|	float	|	Status	|	deltaP	|
|	delw	|	W	|	uint8_t	|	Unknown	|	set this to 0-9 to delete sta config (erases ssid, key, ...)	|
|	dfam	|	R	|	string	|	Constant	|	Devicefamily	|
|	di1	|	R/W	|	bool	|	Config	|	digital Input 1-phase	|
|	die	|	R/W	|	bool	|	Config	|	digital Input Enabled	|
|	dii	|	R/W	|	bool	|	Config	|	digital Input Inverted	|
|	din	|	R	|	uint32_t	|	Status	|	digital input states	|
|	dll	|	R	|	string	|	Status	|	download link for app csv export	|
|	dns	|	R	|	legacy	|	Status	|	dns servers	|
|	dsrc	|	R	|	optional<string>	|	Status	|	inverter data source	|
|	dwo	|	R/W	|	optional<double>	|	Config	|	energy limit, measured in Wh, null means disabled, not the next trip energy	|
|	emx	|	R/W	|	int32_t	|	Config	|	Energymix plugout afterglow in milliseconds.	|
|	err		|	R	|	optional<uint8_t>	|	Status	|	charge ctrl error, null if no connection to charge ctrl established (None=0, F	iAc=1, FiDc=2, Phase=3, Overvolt=4, Overamp=5, Diode=6, PpInvalid=7, GndInvalid=8, ContactorStuck=9, ContactorMiss=10, StatusLockStuckOpen=12, StatusLockStuckLocked=13, FiUnknown=14, Unknown=15, Overtemp=16, NoComm=17, CpInvalid=18) |
|	esk		|	R/W	|	bool	|	Config	|	energy set kwh (for app)	|
|	eto		|	R	|	uint64_t	|	Status	|	energy_total, measured in Wh	|
|	eto_mid	|	R	|	optional<uint64_t>	|	Status	|	MID energy_total, measured in Wh	|
|	evt		|	R	|	optional<string>	|	Status	|	EVCMS transaction id	|
|	facacs	|	R	|	uint8_t	|	Config	|	factory access_control user setting (Open=0, Wait=1, EVCMS=2)	|
|	fhz		|	R	|	optional<float>	|	Status	|	Stromnetz frequency (~50Hz) or 0 if unknown	|
|	fmt		|	R/W	|	int32_t	|	Config	|	minChargeTime in milliseconds	|
|	fna		|	R/W	|	string	|	Config	|	friendlyName	|
|	frc		|	R/W	|	uint8_t	|	Config	|	forceState (Neutral=0, Off=1, On=2)	|
|	frm		|	R/W	|	uint8_t	|	Config	|	roundingMode PreferPowerFromGrid=0, Default=1, PreferPowerToGrid=2	|
|	fsp		|	R/W	|	bool	|	Status	|	force_single_phase	|
|	fsptws	|	R	|	optional<int64_t>	|	Status	|	force single phase toggle wished since	|
|	fst		|	R/W	|	float	|	Config	|	startingPower in watts	|
|	fup		|	R/W	|	bool	|	Config	|	usePvSurplus	|
|	fwv		|	R	|	string	|	Status	|	FW_VERSION	|
|	fzf		|	R/W	|	bool	|	Config	|	zeroFeedin	|
|	gmtr	|	R/W	|	int32_t	|	Config	|	gridMonitoringTimeReconnection in seconds	|
|	gsa		|	R/W	|	optional<int64_t>	|	Status	|	gridMonitoring last failure	|
|	hai		|	R/W	|	bool	|	Config	|	httpApiEnabled (allows /api/status and /api/set requests)	|
|	host	|	R	|	string	|	Status	|	configured hostname	|
|	hsa		|	W	|	bool	|	Config	|	httpStaAuthentication	|
|	ids		|	W	|	optional<JsonObject>	|	Status	|	inverter data setter {"pGrid": 1000., "pPv": 1000., "pAkku": 1000.}	|
|	inva	|	R	|	optional<int64_t>	|	Status	|	age of inverter data	|
|	isgo	|	R	|	bool	|	Constant	|	is go	|										
|	la1		|	R/W	|	uint8_t	|	Config	|	limit adapter 1-phase (in A)	|
|	la3		|	R/W	|	uint8_t	|	Config	|	limit adapter 3-phase (in A)	|
|	lbr		|	R/W	|	uint8_t	|	Config	|	led_bright, 0-255	|
|	lccfc	|	R	|	optional<int64_t>	|	Status	|	lastCarStateChangedFromCharging (in ms)	|
|	lccfi	|	R	|	optional<int64_t>	|	Status	|	lastCarStateChangedFromIdle (in ms)	|
|	lcctc	|	R	|	optional<int64_t>	|	Status	|	lastCarStateChangedToCharging (in ms)	|
|	lcs		|	R	|	int64_t	|	Status	|	last controller scan timestamp in milliseconds since boot time	|
|	led		|	R	|	legacy	|	Status	|	LED animation	|
|	lfspt	|	R	|	optional<int64_t>	|	Status	|	last force single phase toggle	|
|	lmo		|	R/W	|	uint8_t	|	Config	|	logic mode (Default=3, Awattar=4, NextTrip=5)	|
|	lmsc	|	R	|	int64_t	|	Status	|	last model status change	|
|	loa		|	R	|	get: optional<uint8_t> set: u	i	nt8_t | Status		| load balancing ampere	|
|	loc		|	R	|	string	|	Status	|	local time	|
|	loe		|	R/W	|	bool	|	Config	|	Load balancing enabled	|
|	lof		|	R/W	|	uint8_t	|	Config	|	load_fallback	|
|	log		|	R/W	|	string	|	Config	|	load_group_id	|
|	lop		|	R/W	|	uint16_t	|	Config	|	load_priority	|
|	lopr	|	R/W	|	bool	|	Config	|	load balancing protected	|
|	lot		|	R/W	|	get: legacy set: JsonVariantC	o	nst | Config		| load balancing total amp	|
|	loty	|	R/W	|	get: uint8_t set: JsonVariant	C	onst | Config		| load balancing type (Static=false, Dynamic=true)	|
|	lpc		|	R	|	optional<int64_t>	|	Status	|	lastPvCalculation	|
|	lpsc	|	R	|	optional<int64_t>	|	Status	|	last pv surplus calcuation	|
|	lrc		|	R	|	optional<uint8_t>	|	Status	|	last rfid card index	|
|	lri	|	R	|	optional<string>	|	Status	|	last rfid id (only available when sendRfid)	|
|	lrn	|	W	|	uint8_t	|	Config	|	set this to 0-9 to learn last read card id	|
|	lrr	|	R	|	optional<int64_t>	|	Status	|	last rfid read (milliseconds since boot)	|
|	lse	|	R/W	|	bool	|	Config	|	led_save_energy	|
|	lto	|	R	|	int64_t	|	Status	|	local time offset in milliseconds, tab + rbt + lto = local time	|
|	lwf	|	R	|	optional<int64_t>	|	Status	|	last wifi connect failed (milliseconds since boot)	|
|	map	|	R/W	|	get: legacy set: JsonArray	|	Config	|	load_mapping (uint8_t[3])	|
|	mca	|	R/W	|	uint8_t	|	Config	|	minChargingCurrent	|
|	mcc	|	R	|	bool	|	Status	|	MQTT connected	|
|	mcca	|	R	|	optional<int64_t>	|	Status	|	MQTT connected (age)	|
|	mce	|	R/W	|	bool	|	Config	|	MQTT enabled	|
|	mci	|	R/W	|	int32_t	|	Config	|	minimumChargingInterval in milliseconds (0 means disabled)	|
|	mcpd	|	R/W	|	int32_t	|	Config	|	minChargePauseDuration in milliseconds (0 means disabled)	|
|	mcpea	|	R/W	|	optional<int64_t>	|	Config	|	minChargePauseEndsAt (set to null to abort current minChargePauseDuration)	|
|	mcr	|	R/W	|	bool	|	Config	|	MQTT readonly (don't allow api writes from mqtt broker)	|
|	mcs	|	R	|	bool	|	Status	|	MQTT started	|
|	mcu	|	R/W	|	string	|	Config	|	MQTT broker url	|
|	men	|	R/W	|	bool	|	Config	|	modbus slave enabled	|
|	mhe	|	R/W	|	bool	|	Config	|	MQTT enable homeassistant discovery	|
|	mht	|	R/W	|	get: string set: optional<str	i	ng> | Config		| MQTT homeassistant topic prefix (set to null to reset back to the default	)          |
|	mia	|	R	|	legacy	|	Status	|	Modem IP Address	|
|	mlr	|	R	|	optional<string>	|	Status	|	MQTT last error	|
|	mlra	|	R	|	optional<int64_t>	|	Status	|	MQTT last error (age)	|
|	mmp	|	R	|	float	|	Status	|	maximumMeasuredChargingPower	|
|	modelStatus		| R		| uint8_t		| Status		| Reason why we allow charging or not right now (ChargingBecauseNoChargeCtrlDat	a=0, NotChargingBecauseOvertemperature=1, NotChargingBecauseAccessControl=2, ChargingBecauseForceStateOn=3, NotChargingBecauseForceStateOff=4, NotChargingBecauseScheduler=5, NotChargingBecauseEnergyLimit=6, ChargingBecauseAwattarPriceLow=7, ChargingBecauseAutomaticStopTestLadung=8, ChargingBecauseAutomaticStopNotEnoughTime=9, ChargingBecauseAutomaticStop=10, ChargingBecauseAutomaticStopNoClock=11, ChargingBecausePvSurplus=12, ChargingBecauseFallbackV2Default=13, ChargingBecauseFallbackV2Scheduler=14, ChargingBecauseFallbackDefault=15, NotChargingBecauseFallbackV2Awattar=16, NotChargingBecauseFallbackAwattar=17, NotChargingBecauseFallbackAutomaticStop=18, ChargingBecauseCarCompatibilityKeepAlive=19, ChargingBecauseChargePauseNotAllowed=20, NotChargingBecauseSimulateUnplugging=22, NotChargingBecausePhaseSwitch=23, NotChargingBecauseMinPauseDuration=24, NotChargingBecauseError=26, NotChargingBecauseLoadManagementDoesntWant=27, NotChargingBecauseOcppDoesntWant=28, NotChargingBecauseReconnectDelay=29, NotChargingBecauseAdapterBlocking=30, NotChargingBecauseUnderfrequencyControl=31, NotChargingBecauseUnbalancedLoad=32, ChargingBecauseDischargingPvBattery=33, NotChargingBecauseGridMonitoring=34, NotChargingBecauseOcppFallback=35, NotChargingBecauseFloorDetected=36, NotChargingBecauseOcppInoperable=37, NotChargingBecauseUndervoltageControl=38, NotChargingBecauseZeroSetpoint=39) |
|	mptwt	|	R/W	|	int32_t	|	Config	|	min phase toggle wait time (in milliseconds)	|
|	mpwst	|	R/W	|	int32_t	|	Config	|	min phase wish switch time (in milliseconds)	|
|	mqcn	|	R/W	|	bool	|	Config	|	MQTT skipCertCommonNameCheck	|
|	mqg	|	R/W	|	bool	|	Config	|	MQTT useGlobalCaStore	|
|	mqss	|	R/W	|	bool	|	Config	|	MQTT skipServerVerification	|
|	msb	|	R/W	|	bool	|	Config	|	modbus slave swap bytes	|
|	msr	|	R/W	|	bool	|	Config	|	modbus slave swap registers	|
|	mstr	|	R	|	optional<int64_t>	|	Status	|	timestamp of last modbus slave tcp read operation (use rbt to find out how lon	g its ago) |
|	mstw	|	R	|	optional<int64_t>	|	Status	|	timestamp of last modbus slave tcp write operation (use rbt to find out how lo	ng its ago) |
|	mtp	|	R/W	|	get: string set: optional<str	i	ng> | Config		| MQTT topic prefix (set to null to reset back to the default)	|
|	nif	|	R	|	string	|	Status	|	Default route	|
|	nld	|	R	|	uint8_t	|	Constant	|	number of leds	|
|	nmo	|	R/W	|	bool	|	Config	|	norway_mode / ground check enabled when norway mode is disabled	|
|	nrg	|	R	|	legacy	|	Status	|	energy array, U (L1, L2, L3, N), I (L1, L2, L3), P (L1, L2, L3, N, Total), pf	(L1, L2, L3, N) |
|	ocppa	|	R	|	bool	|	Status	|	OCPP connected and accepted	|
|	ocppaa	|	R	|	optional<int64_t>	|	Status	|	OCPP connected and accepted (age)	|
|	ocppai	|	R/W	|	int32_t	|	Config	|	ocppClockAlignedDataInterval	|
|	ocppao	|	W	|	bool	|	Config	|	OCPP AllowOfflineTxForUnknownId	|
|	ocppc	|	R	|	bool	|	Status	|	OCPP connected	|
|	ocppca	|	R	|	optional<int64_t>	|	Status	|	OCPP connected (age)	|
|	ocppcm	|	R/W	|	uint8_t	|	Config	|	OCPP meter values condition (0 = WhenTransactionId, 1 = WhenCharging)	|
|	ocppcn	|	R/W	|	bool	|	Config	|	OCPP skipCertCommonNameCheck	|
|	ocppcs	|	R	|	uint8_t	|	Status	|	OCPP connector status (0=Available, 1=Preparing, 2=Charging, 3=SuspendedEVSE,	4=SuspendedEV, 5=Finishing, 6=Reserved, 7=Unavailable, 8=Faulted) |
|	ocppd	|	R/W	|	string	|	Config	|	OCPP dummy card id (used when no card has been used and charging is already al	lowed / starting) |
|	ocppdp	|	R	|	legacy	|	Status	|	ocpp chargepoint default profiles	|
|	ocppe	|	R/W	|	bool	|	Config	|	OCPP enabled	|
|	ocppf	|	R/W	|	optional<uint8_t>	|	Config	|	OCPP fallback current	|
|	ocppfai	|	W	|	int32_t	|	Config	|	factoryOcppClockAlignedDataInterval	|
|	ocppff	|	R	|	optional<uint8_t>	|	Config	|	OCPP factory fallback current	|
|	ocppg	|	R/W	|	bool	|	Config	|	OCPP useGlobalCaStore	|
|	ocpph	|	R/W	|	int32_t	|	Config	|	ocppHeartbeatInterval	|
|	ocppi	|	R/W	|	int32_t	|	Config	|	ocppMeterValueSampleInterval	|
|	ocppla	|	R/W	|	bool	|	Config	|	OCPP LocalAuthListEnabled	|
|	ocpple	|	R	|	optional<string>	|	Status	|	OCPP last error	|
|	ocpplea	|	R	|	optional<int64_t>	|	Status	|	OCPP last error (age)	|
|	ocpplo	|	R/W	|	bool	|	Config	|	OCPP LocalAuthorizeOffline	|
|	ocppmp	|	R	|	legacy	|	Status	|	ocpp chargepoint max profiles	|
|	ocppr	|	R/W	|	bool	|	Config	|	OCPP rotate phases on charger	|
|	ocpprl	|	R/W	|	bool	|	Config	|	OCPP remote log	|
|	ocpps	|	R	|	bool	|	Status	|	OCPP started	|
|	ocppss	|	R/W	|	bool	|	Config	|	OCPP skipServerVerification	|
|	ocppte	|	R	|	optional<int64_t>	|	Status	|	OCPP transaction ended at (timestamp)	|
|	ocppti	|	R/W	|	optional<int32_t>	|	Status	|	OCPP transaction id	|
|	ocpptp	|	R	|	legacy	|	Status	|	ocpp tx profiles	|
|	ocpptt	|	R/W	|	string	|	Config	|	OCPP tariff text : tariff text string to be used subsequent charging sessions	|
|	ocppu	|	R/W	|	string	|	Config	|	OCPP server url	|
|	oct	|	W	|	JsonVariantConst	|	Config	|	ota from cloud url trigger	|
|	ocu	|	R	|	get: legacy set: JsonVariantC	o	nst | Config		| ota from cloud url, url to download new firmware code from	|
|	oem	|	R	|	string	|	Constant	|	OEM manufacturer	|
|	orsch	|	R/W	|	bool	|	Config	|	OCPP requires same card to halt transactions (as a compatibility mode for shit	ty backends that do not want to follow the ocpp standard) |
|	pakku	|	R	|	optional<float>	|	Status	|	pAkku in W	|
|	pco	|	R/W	|	string	|	Config	|	controllerCloudKey	|
|	pdi	|	R/W	|	bool	|	Config	|	protect Digital Input	|
|	pgr	|	R/W	|	bool	|	Config	|	protect Grid Requirements	|
|	pgrid	|	R	|	optional<float>	|	Status	|	pGrid in W	|
|	pgt	|	R/W	|	float	|	Config	|	pGridTarget in W	|
|	pha	|	R	|	legacy	|	Status	|	phases	|
|	pnp	|	R	|	uint8_t	|	Status	|	numberOfPhases	|
|	po	|	R/W	|	float	|	Config	|	prioOffset in W	|
|	ppv	|	R	|	optional<float>	|	Status	|	pPv in W	|
|	psh	|	R/W	|	float	|	Config	|	phaseSwitchHysteresis in W	|
|	psmd	|	R/W	|	int32_t	|	Config	|	forceSinglePhaseDuration (in milliseconds)	|
|	pvopt_avera	g	ePGrid | R		| float		| Status		| averagePGrid	|
|	pvopt_avera	g	ePPv | R		| float		| Status		| averagePPv	|
|	pvopt_avera	g	ePAkku | R		| float		| Status		| averagePAkku	|
|	pwm	|	R	|	uint8_t	|	Status	|	phase wish mode for debugging / only for pv optimizing / used for timers later	(Force_3=0, Wish_1=1, Wish_3=2) |
|	rbc	|	R	|	uint32_t	|	Status	|	reboot_counter	|
|	rbt	|	R	|	int64_t	|	Status	|	time since boot in milliseconds	|
|	rdbf	|	R/W	|	int32_t	|	Config	|	randomDelayStartFlexibleTariffCharging in seconds	|
|	rdbfe	|	R/W	|	optional<int64_t>	|	Config	|	randomDelayStartFlexibleTariffChargingEndsAt (set to null to abort current ran	domDelayStartFlexibleTariffCharging) |
|	rdbs	|	R/W	|	int32_t	|	Config	|	randomDelayStartScheduledCharging in seconds	|
|	rdbse	|	R/W	|	optional<int64_t>	|	Config	|	randomDelayStartScheduledChargingEndsAt (set to null to abort current randomDe	layStartScheduledCharging) |
|	rde	|	R/W	|	bool	|	Config	|	send rfid serial to cloud/api/mqtt (enable lri api key to show rfid numbers)	|
|	rdef	|	R/W	|	int32_t	|	Config	|	randomDelayStopFlexibleTariffCharging in seconds	|
|	rdefe	|	R/W	|	optional<int64_t>	|	Config	|	randomDelayStopFlexibleTariffChargingEndsAt (set to null to abort current rand	omDelayStopFlexibleTariffCharging) |
|	rdes	|	R/W	|	int32_t	|	Config	|	randomDelayStopScheduledCharging in seconds	|
|	rdese	|	R/W	|	optional<int64_t>	|	Config	|	randomDelayStopScheduledChargingEndsAt (set to null to abort current randomDel	ayStopScheduledCharging) |
|	rdpl	|	R/W	|	int32_t	|	Config	|	randomDelayWhenPluggingCar in seconds	|
|	rdple	|	R/W	|	optional<int64_t>	|	Config	|	randomDelayWhenPluggingCarEndsAt (set to null to abort current randomDelayWhen	PluggingCar) |
|	rdre	|	R/W	|	int32_t	|	Config	|	randomDelayReconnection in seconds	|
|	rdree	|	R/W	|	optional<int64_t>	|	Config	|	randomDelayReconnectionEndsAt (set to null to abort current randomDelayReconne	ction) |
|	rmaf	|	R/W	|	float	|	Config	|	reconnectionMaximumFrequency in Hz	|
|	rmav	|	R/W	|	float	|	Config	|	reconnectionMaximumVoltage in Volt	|
|	rmif	|	R/W	|	float	|	Config	|	reconnectionMinimumFrequency in Hz	|
|	rmiv	|	R/W	|	float	|	Config	|	reconnectionMinimumVoltage in Volt	|
|	rsa	|	R/W	|	optional<int64_t>	|	Status	|	rampup started at	|
|	rsre	|	R/W	|	bool	|	Config	|	rampupAtStartAndReconnectionEnabled	|
|	rsrr	|	R/W	|	float	|	Config	|	rampupAtStartAndReconnectionRate in %/s	|
|	rssi	|	R	|	optional<int8_t>	|	Status	|	RSSI signal strength	|
|	rst	|	W	|	JsonVariantConst	|	Unknown	|	Reset the charger and chargectrl	|
|	scaa	|	R	|	optional<int64_t>	|	Status	|	wifi scan age	|
|	scan	|	R	|	legacy	|	Status	|	wifi scan result (encryptionType: OPEN=0, WEP=1, WPA_PSK=2, WPA2_PSK=3, WPA_WP	A2_PSK=4, WPA2_ENTERPRISE=5, WPA3_PSK=6, WPA2_WPA3_PSK=7) |
|	sch_satur	|	R/W	|	get: legacy set: JsonObject	|	Config	|	scheduler_saturday, control enum values: Disabled=0, Allow=1, Block=2, AllowFr	omGrid=3, BlockFromGrid=4 |
|	sch_sund	|	R/W	|	get: legacy set: JsonObject	|	Config	|	scheduler_sunday, control enum values: Disabled=0, Allow=1, Block=2, AllowFrom	Grid=3, BlockFromGrid=4 |
|	sch_week	|	R/W	|	get: legacy set: JsonObject	|	Config	|	scheduler_weekday, control enum values: Disabled=0, Allow=1, Block=2, AllowFro	mGrid=3, BlockFromGrid=4 |
|	sh	|	R/W	|	float	|	Config	|	stopHysteresis in W	|
|	shut	|	R	|	bool	|	Config	|	is shutter	|
|	simo	|	R	|	bool	|	Config	|	simplified mode	|
|	smd	|	R/W	|	get: legacy set: JsonObject	|	Status	|	smart meter data	|
|	sock	|	R	|	bool	|	Config	|	is socket	|
|	spl3	|	R/W	|	float	|	Config	|	threePhaseSwitchLevel	|
|	sse	|	R	|	string	|	Constant	|	serial number	|
|	styp	|	R	|	string	|	Constant	|	Devicesubtype	|
|	su	|	R/W	|	bool	|	Config	|	simulateUnpluggingShort	|
|	sua	|	R/W	|	bool	|	Config	|	simulateUnpluggingAlways	|
|	sumd	|	R/W	|	int32_t	|	Config	|	simulate unpluging duration (in milliseconds)	|
|	tab	|	R	|	uint64_t	|	Status	|	time at boot in utc in milliseconds, add rbt to get to current utc time	|
|	tcl	|	R/W	|	optional<uint8_t>	|	Config	|	temporary current limit (does not change the user current limit, will be reset	after 10min if not updated regulary) |
|	tds	|	R/W	|	uint8_t	|	Config	|	timezone daylight saving mode, None=0, EuropeanSummerTime=1, UsDaylightTime=2,	AustralianDaylightTime=3 |
|	ten	|	R/W	|	bool	|	Config	|	tamper protection enable	|
|	tlf	|	R	|	bool	|	Status	|	testLadungFinished	|
|	tls	|	R	|	optional<int64_t>	|	Status	|	testLadungStarted	|
|	tma	|	R	|	legacy	|	Status	|	temperature sensors	|
|	tof	|	R/W	|	int32_t	|	Config	|	timezone offset in minutes	|
|	tpa	|	R	|	float	|	Status	|	30 seconds total power average (not used by next-trip, use mmp for next-trip r	elated power) |
|	trx	|	R/W	|	optional<uint8_t>	|	Status	|	transaction, null when no transaction, 0 when without card, otherwise cardInde	x + 1 (1: 0. card, 2: 1. card, ...) |
|	tsi	|	R	|	optional<string>	|	Status	|	transaction start rfidid (only available when sendRfid)	|
|	typ	|	R	|	string	|	Constant	|	Devicetype	|
|	tzt	|	R/W	|	string	|	Config	|	timezone type, freetext string for app selection	|
|	ufa	|	R/W	|	float	|	Config	|	Underfrequency Control activation threshold	|
|	ufe	|	R/W	|	bool	|	Config	|	Underfrequency Control enabled	|
|	ufm	|	R/W	|	uint8_t	|	Config	|	Underfrequency Control mode (TypeNominal=0, TypeActual=1)	|
|	ufs	|	R/W	|	float	|	Config	|	Underfrequency Control stop frequency	|
|	utc	|	R/W	|	string	|	Status	|	utc time	|
|	uve	|	R/W	|	bool	|	Config	|	Undervoltage Control enabled	|
|	uvs	|	R/W	|	int32_t	|	Config	|	Undervoltage Control time in milliseconds	|
|	uvt	|	R/W	|	float	|	Config	|	Undervoltage Control threshold in Volt	|
|	var	|	R	|	uint8_t	|	Constant	|	variant: max Ampere value of unit (11: 11kW/16A, 22: 22kW/32A)	|
|	wb	|	R	|	optional<double>	|	Status	|	power BATTERY in W	|
|	wbw	|	R	|	uint32_t	|	Config	|	WiFi Bandwidth (for both AP and STA) WIFI_BW_HT20=1, WIFI_BW_HT40=2	|
|	wda	|	R/W	|	bool	|	Config	|	disable AccessPoint when cloud is connected	|
|	wg	|	R	|	optional<double>	|	Status	|	power GRID in W	|
|	wh	|	R	|	double	|	Status	|	energy in Wh since car connected	|
|	wh_mid	|	R	|	optional<double>	|	Status	|	MID energy in Wh since car connected	|
|	whb	|	R	|	double	|	Status	|	energy BATTERY in Wh since car connected	|
|	whg	|	R	|	double	|	Status	|	energy GRID in Wh since car connected	|
|	who	|	R	|	double	|	Status	|	energy OTHER in Wh since car connected	|
|	whs	|	R	|	double	|	Status	|	energy SOLAR in Wh since car connected	|
|	wifis	|	R/W	|	get: legacy set: JsonArray	|	Config	|	wifi configurations with ssids and keys, if you only want to change the second	entry, send an array with 1 empty and 1 filled wifi config object: [{}, {"ssid":"","key":""}] |
|	wo	|	R	|	optional<double>	|	Status	|	power OTHER in W	|
|	ws	|	R	|	optional<double>	|	Status	|	power SOLAR in W	|
|	wsc	|	R	|	uint8_t	|	Status	|	WiFi STA error count	|
|	wsl	|	R	|	legacy	|	Status	|	WiFi STA error messages log	|
|	wsms	|	R	|	uint8_t	|	Status	|	WiFi state machine state (None=0, Scanning=1, Connecting=2, Connected=3)	|
|	wst	|	R	|	uint8_t	|	Status	|	WiFi STA status (IDLE_STATUS=0, NO_SSID_AVAIL=1, SCAN_COMPLETED=2, CONNECTED=3	, CONNECT_FAILED=4, CONNECTION_LOST=5, DISCONNECTED=6, CONNECTING=7, DISCONNECTING=8, NO_SHIELD=9, WAITING_FOR_IP=10 (for compatibility with WiFi Shield library)) |
|	zfo	|	R/W	|	float	|	Config	|	zeroFeedinOffset in W	|

