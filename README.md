# KPF-etc
README.md

This repository contains a set of pre-calculated photon-limited velocity uncertainties for the Keck Planet Finder project, as well as a simple IDL lookup function for quickly estimating photon-limited RV precision for a user-specified target observation.

The model grid descriptions are as follows:

	'dv_uncertainty_master_order.fits':  order-by-order velocity uncertainites [m/s] (4D grid, Teff x Vmag x Exposure time x Echelle order)
    'dv_uncertainty_master.fits': 		 integrated KPF velocity uncertainty values [m/s] (3D grid, Teff x Vmag x Exposure time)
	'snr_master_order.fits':		  	 mean order-by-order SNR values (4d grid, Teff x Vmag x Exposure time x Echelle order)

The basis arrays used to generate the grids are contained in these files:

	'order_wvl_centers.fits': 			 mean wavelengths of echelle orders [nm]
	'photon_grid_teff.fits':			 stellar effective temperature array [K]
	'photon_grid_vmag.fits':			 stellar V magnitude
	'photon_grid_exptime.fits':			 exposure time array [s]

The precomputed grids were calculated assuming parameter bounds of:

	- Teff: 2700 - 6600 Kelvin
	- Vmag: 5 - 19
	- Texp: 10 - 3600 seconds
	
Interpolating beyond these bounds will result in errors in the returned RV values.
	
All calculations are based on BT-Settl synthetic stellar spectra, available at: http://phoenix.astro.physik.uni-goettingen.de/?page_id=15

Current grid uses the KPF PDR throughput model, a median WMKO atmospheric transmission curve (Buton et al 2012), and excludes regions of the spectrum with 1% or deeper telluric features (based on telfit model).