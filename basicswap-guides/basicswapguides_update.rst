================
Update BasicSwap
================

.. title::
   BasicSwap DEX Update Guide
   
.. meta::
   :description lang=en: Learn how to update your BasicSwap instance.
   :keywords lang=en: Particl, DEX, Trading, Exchange, Buy Crypto, Sell Crypto, Installation, Quickstart, Blockchain, Privacy, E-Commerce, multi-vendor marketplace, online marketplace

:term:`BasicSwap DEX <BasicSwap>` is an open-source work in progress, and, as such, constant and regular updates are to be expected.

To benefit from new features, improvements, and bug fixes, it is recommended that you update your BasicSwap instance frequently.

This guide will show you how to update BasicSwap properly.

----

.. contents:: Table of Contents
   :local:
   :backlinks: none
   :depth: 2

----

Update a Docker Image
=====================

If you've built :term:`BasicSwap` using the Docker method, follow these steps to update your instance to the most up-to-date version.

.. tabs::

     .. group-tab:: Update BasicSwap

       Update BasicSwap to the most up-to-date version. 

        .. rst-class:: bignums

             #. Navigate to your BasicSwap's docker folder (where BasicSwap is installed).

                .. code-block:: bash

                   cd basicswap/docker

             #. Make sure BasicSwap is stopped.

                .. code-block:: bash

                   docker-compose stop

             #. Pull the latest BasicSwap updates from Github.

                .. code-block:: bash

                   git pull

             #. Apply the updates you've pulled from Github to your docker image.

                .. code-block:: bash

                   export COINDATA_PATH=/var/data/coinswaps && docker-compose build

                If BasicSwap's dependencies have changed, the update must be applied with the :guilabel:`--no-cache` argument.

                   .. code-block:: bash

                      COINDATA_PATH=/var/data/coinswaps && docker-compose build --no-cache

             #. Launch BasicSwap

                .. code-block:: bash

                   docker-compose up

       .. attention::

          If updating from versions below 0.21, you may need to add :guilabel:`wallet=wallet.dat` to the core config.


     .. group-tab:: Update Coin Core Versions

       Update the core version of one or more coins you've enabled on BasicSwap. You need to first update BasicSwap before you can update coin cores.

        .. rst-class:: bignums

             #. Make sure your BasicSwap instance if up-to-date with the latest updates.

             #. Navigate to your BasicSwap docker folder (where your BasicSwap docker image is located).

                .. code-block:: bash

                   cd basicswap/docker

             #. Make sure BasicSwap is stopped.

                .. code-block:: bash

                   docker-compose stop

             #. Apply coin core updates to your docker image. Make sure to write what coin core(s) you want to update using the :guilabel:`--withcoins` argument.

                .. code-block:: bash

                   docker-compose run --rm swapclient \ 

                      basicswap-prepare --datadir=/coindata --preparebinonly --withcoins=monero,bitcoin

       .. attention::

          If updating from versions below 0.21, you may need to add :guilabel:`wallet=wallet.dat` to the core config.

Update Without Docker
=====================

If you've built :term:`BasicSwap` without using the Docker method, follow these steps to update your instance to the most up-to-date version.

.. tabs::

     .. group-tab:: Update BasicSwap

       Update BasicSwap to the most up-to-date version. 

        .. rst-class:: bignums

             #. Properly shutdown BasicSwap.

             #. Prepare your BasicSwap to receive updates by executing these two commands **one by one**.

                .. code-block:: bash

                   export SWAP_DATADIR=/Users/$USER/coinswaps
                   . $SWAP_DATADIR/venv/bin/activate && python -V

             #. Navigate to your BasicSwap folder.

                .. code-block:: bash

                   cd $SWAP_DATADIR/basicswap

             #. Pull the latest BasicSwap updates from Github.

                .. code-block:: bash

                   git pull

             #. Apply the updates to your BasicSwap instance

                .. code-block:: bash

                   pip3 install .

       .. attention::

          If updating from versions below 0.21, you may need to add :guilabel:`wallet=wallet.dat` to the core config.

     .. group-tab:: Update Coin Core Versions

       Update the core version of the coins you've enabled on BasicSwap. Note that you need to first update BasicSwap before you can update individual coin cores.

        .. rst-class:: bignums

             #. Properly shutdown BasicSwap.
             
             #. Make sure your BasicSwap instance is up-to-date with the latest updates.

             #. Apply coin core updates to your BasicSwap instance. Make sure to input what coin core(s) you want to update using the :guilabel:`--withcoins` argument.

                .. code-block:: bash

                   basicswap-prepare --datadir=$SWAP_DATADIR -preparebinonly --withcoins=monero,bitcoin

       .. attention::

          If updating from versions below 0.21, you may need to add :guilabel:`wallet=wallet.dat` to the core config.

----

.. seealso::

 - BasicSwap Explained - :doc:`BasicSwap Explained <../basicswap-dex/basicswap_explained>`
 - BasicSwap Guides - :doc:`Install BasicSwap <../basicswap-guides/basicswapguides_installation>`
 - BasicSwap Guides - :doc:`Route BasicSwap Through Tor <../basicswap-guides/basicswapguides_update>`
 - BasicSwap Guides - :doc:`Make an Offer <../basicswap-guides/basicswapguides_make>`
 - BasicSwap Guides - :doc:`Take an Offer <../basicswap-guides/basicswapguides_take>`