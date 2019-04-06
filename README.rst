In terminal 1:

.. code-block:: none

  > cmake -H. -B_builds/OpenCV -DPKG=OpenCV

Check root is locked:

.. code-block:: none

  -- [hunter *** DEBUG *** ] Package 'OpenCV' CONFIGURATION_TYPES: Release;Debug
  -- [hunter *** DEBUG *** ] Package 'OpenCV' is cacheable: YES
  -- [hunter *** DEBUG *** ] Install to: /.../deadlock-test/__HUNTER/_Base/68657b8/81d2ad6/8321d13/Install
  -- [hunter] OPENCV_ROOT: /.../deadlock-test/__HUNTER/_Base/68657b8/81d2ad6/8321d13/Install (ver.: 4.0.0-p0)
  -- [hunter *** DEBUG *** ] Locking directory: /.../deadlock-test/__HUNTER/_Base/Download/OpenCV/4.0.0-p0/90680ea
  -- [hunter *** DEBUG *** ] Lock done
  -- [hunter *** DEBUG *** ] Already locked: /.../deadlock-test/__HUNTER/_Base/Download/OpenCV/4.0.0-p0/90680ea
  -- [hunter *** DEBUG *** ] Locking directory: /.../deadlock-test/__HUNTER/_Base/68657b8/81d2ad6/8321d13 # <<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
  -- [hunter *** DEBUG *** ] Lock done                                                                    # <<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
  -- [hunter *** DEBUG *** ] Package 'OpenCV' default arguments: 'BUILD_ANDROID_EXAMPLES=OFF;BUILD_JAVA=OFF;BUILD_DOCS=OFF;BUILD_EXAMPLES=OFF;BUILD_PERF_TESTS=OFF;BUILD_TESTS=OFF;BUILD_opencv_apps=OFF;INSTALL_PYTHON_EXAMPLES=OFF;BUILD_WITH_STATIC_CRT=OFF;BUILD_ZLIB=OFF;BUILD_TIFF=OFF;BUILD_PNG=OFF;BUILD_JPEG=OFF;BUILD_JASPER=OFF;BUILD_WEBP=OFF;BUILD_opencv_java=OFF;BUILD_opencv_python2=OFF;BUILD_opencv_python3=OFF;WITH_CUDA=OFF;WITH_CUFFT=OFF;BUILD_opencv_dnn=OFF;WITH_OPENEXR=OFF'

And in terminal 2:

.. code-block:: none

  > cmake -H. -B_builds/PNG -DPKG=PNG

In terminal 2 the ``Download/PNG`` lock acquired and we will be waiting for root lock:

.. code-block:: none

  -- [hunter *** DEBUG *** ] Locking directory: /.../deadlock-test/__HUNTER/_Base/Download/PNG/1.6.26-p3/fcaaae4
  -- [hunter *** DEBUG *** ] Lock done
  -- [hunter *** DEBUG *** ] Already locked: /.../deadlock-test/__HUNTER/_Base/Download/PNG/1.6.26-p3/fcaaae4
  -- [hunter *** DEBUG *** ] Locking directory: /.../deadlock-test/__HUNTER/_Base/68657b8/81d2ad6/8321d13

In terminal 1 we will reach PNG build and will wait for ``Download/PNG`` lock:

.. code-block:: none

  -- [hunter *** DEBUG (CACHE RUN) *** ] Already locked: /.../deadlock-test/__HUNTER/_Base/68657b8/81d2ad6/8321d13
  -- [hunter *** DEBUG (CACHE RUN) *** ] Already locked: /.../deadlock-test/__HUNTER/_Base/Download/WebP/1.0.2-p3/f29c535
  -- [hunter *** DEBUG (CACHE RUN) *** ] Locking directory: /.../deadlock-test/__HUNTER/_Base/Download/PNG/1.6.26-p3/fcaaae4
