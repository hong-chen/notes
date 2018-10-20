Read RGB Imagery (Cropped PNG file from NASA WorldView)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

::

    import numpy as np
    import matplotlib.image as mpl_img

    fname   = 'image.png'
    rgb_img = mpl_img.imread(fname)


===============================================
Create longitude, latitude for the image pixels
===============================================

::

    # 'extent' indicates the region of the image
    # The four values should follow the order of
    # [lon_left, lon_right, lat_bottom, lat_top]
    extent    = [100.0, 120.0, 40.0, 42.0]

    Ny, Nx, _ = rgb_img.shape
    rgb_img = mpl_img.imread(fname)

    x0 = np.linspace(extent[0], extent[1], Nx+1)
    y0 = np.linspace(extent[3], extent[2], Ny+1)

    x  = (x0[1:]+x0[:-1])/2.0
    y  = (y0[1:]+y0[:-1])/2.0

    lon_img, lat_img = np.meshgrid(x, y)




Read HDF4 File
~~~~~~~~~~~~~~

::

    from pyhdf.SD import SD, SDC

    fname = 'MYD03.A2015247.1805.061.2018051034504.hdf'
    f     = SD(fname, SDC.READ)
    lon_modis = f.select('Longitude').get()
    lat_modis = f.select('Latitude').get()
    f.end()

    fname     = 'MYD06_L2.A2015247.1805.061.2018052184944.hdf'
    f         = SD(fname, SDC.READ)
    cot_obj   = f.select('Cloud_Optical_Thickness')
    attrs     = cot_obj.attributes()
    cot_modis = cot_obj.get()*attrs['scale_factor'] + attrs['add_offset']
    f.end()


Read netCDF4 File
~~~~~~~~~~~~~~~~~

::

    import netCDF4 as nc4

    fname = 'MERRA2_400.inst1_2d_asm_Nx.20150904.nc4'
    f     = nc4.Dataset(fname, 'r')
    lon_merra = f.variables['lon'][...]
    lat_merra = f.variables['lat'][...]
    t2m_merra = f.variables['T2M'][...]
    f.close()

Read HDF5 File
~~~~~~~~~~~~~~~~~

::

    import h5py

    fname = 'data_all.h5'
    f     = h5py.File(fname, 'r')
    lon_img = f['lon_img'][...]
    lat_img = f['lat_img'][...]
    rgb_img = f['rgb_img'][...]
    f.close()
