#################
Sigenergy Sigenstor with Gateway
#################

.. note::
   The sensors utilised below are provided by the 'Sigenergy Local Modbus' integration, maintained at: https://github.com/TypQxQ/Sigenergy-Local-Modbus
   If there is enough interest for a version using the MQTT version, maintained at: https://github.com/seud0nym/sigenergy2mqtt, I will see about adding.

______________________________________________________________


*****************************
Minimal Configuration (Solar and Battery)
*****************************

.. code-block:: yaml
  :linenos:

  type: custom:sunsynk-power-flow-card
  cardstyle: full
  show_solar: true
  wide: false
  show_battery: true
  show_grid: true
  dynamic_line_width: true
  decimal_places_energy: 1
  inverter:
    model: sigenergy
    three_phase: true
    modern: false
    autarky: energy
    auto_scale: false
  battery:
    shutdown_soc: number.sigen_plant_ess_backup_state_of_charge
    show_daily: true
    invert_power: true
    dynamic_colour: true
    animate: true
    remaining_energy_to_shutdown: false
    show_remaining_energy: true
    count: 1
    soc_decimal_places: 1
    auto_scale: false
    linear_gradient: true
    show_absolute: false
    max_power: sensor.sigen_plant_ess_rated_charging_power
    shutdown_soc_offgrid: sensor.sigen_plant_discharge_cut_off_soc
    soc_end_of_charge: sensor.sigen_plant_charge_cut_off_soc
    energy: sensor.sigen_plant_rated_energy_capacity
  solar:
    show_daily: true
    display_mode: 2
    mppts: 3
    max_power: 29999                                                           # Update with max power of your inverter, currently this is setup for a Sig 30kW EC
    auto_scale: false
    pv1_name: PV 1
    pv2_name: PV 2
    pv3_name: PV 3
    pv4_name: PV 4
    pv1_max_power: 10000                                                       # Update with size in watts of your MPPT 1 string
    pv2_max_power: 5500                                                        # Update with size in watts of your MPPT 2 string
    pv3_max_power: 10000                                                       # Update with size in watts of your MPPT 3 string
    pv4_max_power: 0                                                           # Update with size in watts of your MPPT 4 string
    dynamic_colour: false
    efficiency: 3
  load:
    show_daily: true
    auto_scale: false
    invert_flow: false
    show_aux: false
    max_power: 12000
    additional_loads: 6
    load1_name: Load 1
    load1_icon: ""
    load2_name: Load 2
    load2_icon: ""
    load3_name: Load 3
    load3_icon: ""
    load4_name: Load 4
    load4_icon: ""
    load5_name: Load 5
    load5_icon: mdi:server-network
    load6_name: Load 6
    load6_icon: ""
    dynamic_icon: true
    dynamic_colour: true
    invert_load: false
  grid:
    show_daily_buy: true
    show_daily_sell: true
    show_nonessential: true
    auto_scale: false
    grid_name: Grid Name                                                       # Update with the name of your energy retailer or grid
    colour: "#ff0000"
    grid_off_colour: "#9e9e9e"
    export_colour: limegreen
    energy_cost_decimals: 2
    import_icon: mdi:transmission-tower-import
    export_icon: mdi:transmission-tower-export
    disconnected_icon: mdi:transmission-tower-off
    nonessential_icon: ""
    load1_name: HVAC
    additional_loads: 3
    load1_icon: mdi:air-conditioner
    load2_icon: mdi:tumble-dryer
    load2_name: Dryer
    load3_name: Washer
    load3_icon: mdi:washing-machine
  entities:
    aux_power_166: none
    battery_current_191: none
    battery_power_190: sensor.sigen_plant_battery_power
    battery_soc_184: sensor.sigen_plant_battery_state_of_charge
    battery_temp_182: sensor.sigen_inverter_battery_maximum_temperature
    battery_voltage_183: sensor.sigen_inverter_battery_average_cell_voltage
    day_aux_energy: sensor.emhass_deferrable_loads_total
    day_battery_charge_70: sensor.sigen_plant_daily_battery_charge_energy
    day_battery_discharge_71: sensor.sigen_plant_daily_battery_discharge_energy
    day_grid_export_77: sensor.sigen_plant_daily_grid_export_energy
    day_grid_import_76: sensor.sigen_plant_daily_grid_import_energy
    day_load_energy_84: sensor.sigen_plant_daily_consumed_energy
    day_pv_energy_108: sensor.sigen_inverter_daily_pv_energy
    dc_transformer_temp_90: sensor.sigen_inverter_pcs_internal_temperature
    energy_cost_buy: sensor.amber_general_forecast                            # Update with your electricity BUY cost sensor
    energy_cost_sell: sensor.amber_feed_in_forecast                           # Update with your electricity SELL cost sensor
    environment_temp: sensor.your_location_temp                               # Update with your locations weather feed
    essential_load1: none                                                     # Update with an essential load power sensor
    essential_load1_extra: none                                               # Update with an essential load energy or other sensor
    essential_load2: none                                                     # Update with an essential load power sensor
    essential_load2_extra: none                                               # Update with an essential load energy or other sensor
    essential_load3: none                                                     # Update with an essential load power sensor
    essential_load3_extra: none                                               # Update with an essential load energy or other sensor
    essential_load4: none                                                     # Update with an essential load power sensor
    essential_load5_extra: none                                               # Update with an essential load energy or other sensor
    essential_load5: none                                                     # Update with an essential load power sensor
    essential_load5_extra: none                                               # Update with an essential load energy or other sensor
    essential_load6: none                                                     # Update with an essential load power sensor
    essential_load6_extra: none                                               # Update with an essential load energy or other sensor
    essential_power: sensor.sigen_plant_consumed_power
    grid_connected_status_194: sensor.sensor.sigen_plant_grid_connection_status
    grid_ct_power_172: sensor.none
    grid_ct_power_total: sensor.sigen_plant_grid_active_power
    grid_frequency: sensor.sigen_inverter_grid_frequency
    grid_power_169: sensor.sigen_plant_grid_active_power
    grid_voltage: sensor.sigen_inverter_rated_grid_voltage
    inverter_current_164: sensor.sigen_inverter_phase_a_current
    inverter_current_L2: sensor.sigen_inverter_phase_b_current
    inverter_current_L3: sensor.sigen_inverter_phase_c_current
    inverter_power_175: sensor.sigen_inverter_active_power
    inverter_status_59: sensor.sigen_plant_plant_running_state
    inverter_voltage_154: sensor.sigen_inverter_phase_a_voltage
    inverter_voltage_L2: sensor.sigen_inverter_phase_b_voltage
    inverter_voltage_L3: sensor.sigen_inverter_phase_c_voltage
    load_frequency_192: sensor.sigen_inverter_grid_frequency
    max_sell_power: number.sigen_plant_grid_export_limitation
    non_essential_load: sensor.gpo_clothes_dryer_active_power                 # Update with a non-essential load you have a power sensor for.
    non_essential_load2: sensor.gpo_clothes_dryer_active_power                # Update with a non-essential load you have a power sensor for.
    non_essential_load3: sensor.washing_machine_power                         # Update with a non-essential load you have a power sensor for.
    nonessential_power: sensor.emhass_deferrable_loads_power                  # Note: This is a Helper sensor group, you need to create with all your non-essential loads 'Power' sensors as members.
    priority_load_243: none
    pv1_current_110: sensor.sigen_inverter_pv1_current
    pv1_power_186: sensor.sigen_inverter_pv1_power
    pv1_voltage_109: sensor.sigen_inverter_pv1_voltage
    pv2_current_112: sensor.sigen_inverter_pv2_current
    pv2_power_187: sensor.sigen_inverter_pv2_power
    pv2_voltage_111: sensor.sigen_inverter_pv2_voltage
    pv3_current_114: sensor.sigen_inverter_pv3_current
    pv3_power_188: sensor.sigen_inverter_pv3_power
    pv3_voltage_113: sensor.sigen_inverter_pv3_voltage
    pv4_current_116: sensor.sigen_inverter_pv4_current
    pv4_power_189: sensor.sigen_inverter_pv4_power
    pv4_voltage_115: sensor.sigen_inverter_pv4_voltage
    remaining_solar: sensor.energy_production_today_remaining_total           # Use Solcast or Forecast Solar integration to create a sensor such as this.
    solar_sell_247: binary_sensor.sigen_plant_exporting_to_grid
    total_pv_generation: sensor.sigen_plant_total_pv_energy
    use_timer_248: none


*****************************
Minimal Configuration (Solar, Battery and AC EV Charger)
*****************************

    PENDING Access to a Home Assistance instance with a Sigenergy AC EV charger to test against.



*****************************
Minimal Configuration (Solar, Battery and DC EV Charger)
*****************************

.. code-block:: yaml
  :linenos:

  type: custom:sunsynk-power-flow-card
  cardstyle: full
  show_solar: true
  wide: true
  show_battery: true
  show_grid: true
  dynamic_line_width: true
  decimal_places_energy: 1
  inverter:
    model: sigenergy
    three_phase: true
    modern: false
    autarky: energy
    auto_scale: true
  battery:
    shutdown_soc: number.sigen_plant_ess_backup_state_of_charge
    show_daily: true
    invert_power: true
    dynamic_colour: true
    animate: true
    remaining_energy_to_shutdown: false
    show_remaining_energy: true
    count: 1
    soc_decimal_places: 1
    auto_scale: true
    linear_gradient: true
    show_absolute: false
    max_power: sensor.sigen_plant_ess_rated_discharging_power
    shutdown_soc_offgrid: sensor.sigen_plant_discharge_cut_off_soc
    soc_end_of_charge: sensor.sigen_plant_charge_cut_off_soc
    energy: sensor.sigen_plant_rated_energy_capacity
    hide_soc: true
    invert_flow: false
    colour: "#6fa54a"
  solar:
    show_daily: true
    display_mode: 2
    mppts: 4
    auto_scale: true
    pv1_name: PV 1
    pv2_name: PV 2
    pv3_name: PV 3
    pv2_max_power: 1000
    pv3_max_power: 1000
    dynamic_colour: true
    efficiency: 3
    pv4_max_power: 15000
    max_power: 15000
  load:
    show_daily: true
    auto_scale: true
    invert_flow: false
    show_aux: true
    max_power: 12000
    additional_loads: 2
    load1_icon: mdi:water-boiler
    load2_name: Fridge
    load3_name: Load 3
    load4_name: Load 4
    load5_name: Load 5
    load6_name: Load 6
    load1_name: Hot Water
    dynamic_icon: true
    dynamic_colour: true
    invert_load: false
    load5_icon: mdi:server-network
    aux_type: mdi:car-electric-outline
    aux_load1_icon: mdi:car-electric
    aux_load2_icon: mdi:car-electric-outline
    aux_colour: "#cb4fe3"
    show_absolute_aux: false
    aux_dynamic_colour: true
    show_daily_aux: true
    aux_loads: 2
    aux_load1_name: EV1 (60 kWh)
    aux_load2_name: EV2 (55 kWh)
    aux_daily_name: DAILY DISCHARGE V2X
    load2_icon: mdi:fridge
  grid:
    show_daily_buy: true
    show_daily_sell: true
    show_nonessential: true
    auto_scale: true
    grid_name: Grid
    colour: "#5385f9"
    grid_off_colour: "#9e9e9e"
    import_icon: mdi:transmission-tower-import
    export_icon: mdi:transmission-tower-export
    disconnected_icon: mdi:transmission-tower-off
    nonessential_icon: ""
    load1_name: HVAC
    additional_loads: 3
    load1_icon: mdi:air-conditioner
    load2_icon: mdi:car-electric-outline
    load2_name: EVx2
    load3_name: Pool
    load3_icon: mdi:pool-thermometer
    energy_cost_decimals: 2
    nonessential_name: Deferrable Loads
    show_absolute: false
  entities:
    use_timer_248: switch.sunsynk_toggle_system_timer
    priority_load_243: switch.sunsynk_toggle_priority_load
    inverter_current_164: sensor.sigen_inverter_phase_a_current
    inverter_current_L2: sensor.sigen_inverter_phase_b_current
    inverter_current_L3: sensor.sigen_inverter_phase_c_current
    inverter_power_175: sensor.sigen_inverter_active_power
    grid_connected_status_194: sensor.sigen_plant_grid_connection_status
    inverter_status_59: sensor.sigen_plant_plant_running_state
    day_battery_charge_70: sensor.sigen_plant_daily_battery_charge_energy
    day_battery_discharge_71: sensor.sigen_plant_daily_battery_discharge_energy
    battery_voltage_183: sensor.sigen_inverter_battery_average_cell_voltage
    battery_soc_184: sensor.sigen_plant_battery_state_of_charge
    battery_power_190: sensor.sigen_plant_battery_power
    battery_current_191: none
    battery_temp_182: sensor.sigen_inverter_battery_maximum_temperature
    day_grid_import_76: sensor.sigen_plant_daily_grid_import_energy
    day_grid_export_77: sensor.sigen_plant_daily_grid_export_energy
    grid_ct_power_172: sensor.sigen_plant_grid_phase_a_active_power
    essential_load2: sensor.fridge_power
    solar_sell_247: binary_sensor.sigen_plant_exporting_to_grid
    pv1_power_186: sensor.sigen_inverter_pv1_power
    pv1_voltage_109: sensor.sigen_inverter_pv1_voltage
    pv1_current_110: sensor.sigen_inverter_pv1_current
    pv2_power_187: sensor.sigen_inverter_pv2_power
    pv2_voltage_111: sensor.sigen_inverter_pv2_voltage
    pv2_current_112: sensor.sigen_inverter_pv2_current
    pv3_power_188: sensor.sigen_inverter_pv3_power
    pv3_voltage_113: sensor.sigen_inverter_pv3_voltage
    pv3_current_114: sensor.sigen_inverter_pv3_current
    grid_ct_power_total: sensor.sigen_plant_grid_active_power
    grid_voltage: sensor.sigen_inverter_rated_grid_voltage
    grid_frequency: sensor.sigen_inverter_grid_frequency
    inverter_voltage_154: sensor.sigen_inverter_phase_a_voltage
    inverter_voltage_L2: sensor.sigen_inverter_phase_b_voltage
    inverter_voltage_L3: sensor.sigen_inverter_phase_c_voltage
    load_frequency_192: sensor.sigen_inverter_grid_frequency
    grid_power_169: sensor.sigen_plant_grid_active_power
    max_sell_power: number.sigen_plant_grid_export_limitation
    essential_load5: sensor.it_hardware_active_power
    non_essential_load1: sensor.hvac_power
    non_essential_load2: sensor.ev_power
    non_essential_load3: sensor.pool_power
    energy_cost_buy: sensor.amber_general_price
    energy_cost_sell: sensor.amber_feed_in_price
    dc_transformer_temp_90: sensor.sigen_inverter_pcs_internal_temperature
    essential_load5_extra: sensor.it_hardware_energy_daily
    total_pv_generation: sensor.sigen_plant_daily_third_party_inverter_energy
    day_pv_energy_108: sensor.sigen_plant_daily_third_party_inverter_energy
    pv4_power_189: sensor.sigen_plant_third_party_pv_power
    grid_ct_power_L2: sensor.sigen_plant_grid_phase_b_active_power
    grid_ct_power_L3: sensor.sigen_plant_grid_phase_c_active_power
    environment_temp: sensor.tewantin_temp
    remaining_solar: sensor.solcast_pv_forecast_forecast_remaining_today
    load_power_L1: sensor.phase_a_load
    load_power_L2: sensor.phase_b_load
    load_power_L3: sensor.phase_c_load
    aux_power_166: sensor.sigen_inverter_dc_charger_output_power
    aux_load2: sensor.my_t_battery_level
    aux_load2_extra: sensor.my_t_pack_current
    aux_connected_status: switch.charge_control
    aux_load1_extra: sensor.m3p_t_pack_current
    aux_load1: sensor.m3p_t_battery_level
    essential_load1: sensor.hws_power
    nonessential_power: sensor.non_essential_circuits_power
    essential_power: sensor.power_load_no_var_loads
    day_aux_energy: sensor.evdc_daily_discharge
    day_load_energy_84: sensor.sigen_plant_daily_load_consumption
  grid_options:
    columns: full
    rows: 8
  decimal_places: 1



*****************************
Minimal Configuration (Solar, Battery and Generator)
*****************************

    PENDING Access to a Home Assistance instance with a Sigenergy Gateway with a Generator wired in, to test against.
