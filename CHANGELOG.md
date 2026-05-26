# Changelog

## 1.2.0.0
- 5/26/2026 GEO/DVP. Added new attributes, classes, and enum values to support upcoming F-BIDR bundle.
    - New class BIDR_Clock_Conversion, using new attributes clock_intercept_coeff, clock_slope_coeff, clock_utc_to_j2000_correction_factor and reference_sclk_factor.
    - New class BIDR_Keplerians, using new attributes orbit_argument_of_periapsis, orbit_ascending_node_lon, orbit_eccentricity, orbit_inclination, orbit_period, orbit_semimajor, predicted_periapsis_sclk and predicted_periapsis_tdb.
    - New class Orbit_Metadata, using new attributes mapping_start_time_tdb, mapping_start_time_utc, mapping_stop_time_tdb, mapping_stop_time_utc, oblique_sinusoidal_start_time_tdb, oblique_sinusoidal_start_time_utc, oblique_sinusoidal_stop_time_tdb and oblique_sinusoidal_stop_time_utc.
    - New classes X_Axis, Y_Axis, and Z_Axis, each using new attributes x, y, and z.
    - New class BIDR_Oblique_Sinusoidal_Frame_Axes, using above new classes X_Axis, Y_Axis, and Z_Axis.
    - New class BIDR_Parameters, using new attributes nav_uid_ephemeris_file, pixel_size, projection_name, projection_origin_lat, projection_origin_lon and total_bursts, and above new classes Orbit_Metadata, BIDR_Keplerians, BIDR_Clock_Conversion and BIDR_Oblique_Sinusoidal_Frame_Axes.
    - New permissible values for the existing mission_phase_name attribute Cruise, Orbit Insertion and Orbit Checkout.

## 1.1.0.0
- 12/4/2024 GEO/EIS. Added band_name, dsn_station_number, organization_id, and 
    received_polarization_type.

## 1.0.0.0

- 09/26/2023 GEO/EAG. Renamed attribute pds3_volume_id to original_pds_volume_id because many
    Magellan datasets were created using standards that predate PDS3

- 11/23/2021 GEO/EAG. Initial version
