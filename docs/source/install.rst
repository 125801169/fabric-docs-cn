安装示例、二进制文件和Docker镜像
==============================

在我们为Hyperledger Fabric二进制文件开发真正的安装程序时，我们提供了一个脚本，可以下载并安装样例和二进制文件到您的系统。 我们认为您会发现安装的示例应用程序可以帮助去了解Hyperledger Fabric有关的功能和运维的更多信息。

.. note:: 如果您在 **Windows** 上运行样例，则需要使用 Docker 快速启动终端来执行即将发布的终端命令。如果您之前没有安装，请访问 :doc:`prereqs` 。

          如果您在 Windows 7 或 macOS 上使用 Docker Toolbox， 您在安装和运行示例需要使用到 ``C:\Users`` （Windows 7）或 ``/Users`` （macOS）目录下的路径。

          如果您在 Mac 上使用 Docker，则需要使用到 ``/Users``、 ``/Volumes``、 ``/private``、 或 ``/tmp`` 这些目录下的路径。 要使用其他路径，请参阅 Docker 文档以获取 `文件共享 <https://docs.docker.com/docker-for-mac/#file-sharing>`__ 。

          如果您在 Windows 下使用 Docker，请参阅 Docker 文档以获取 `共享驱动器 <https://docs.docker.com/docker-for-windows/#shared-drives>`__ ，并使用其中一个共享驱动器下的路径。

.. note:: 如果你是在 **Mac** 上运行，在运行之前可能需要安装 ``wget``。``wget`` 命令被用来从 GitHub releases 下载 binaries。使用 ``brew install wget`` 来安装 wget。

确定计算机上要放置 `fabric-samples` 仓存的位置，并在终端窗口中进入该目录。 按以下步骤执行相关命令：

#. 如果需要，克隆 `hyperledger/fabric-samples <https://github.com/hyperledger/fabric-samples>`_ 仓库
#. 检出适当的版本标签
#. 将指定版本的Hyperledger Fabric平台特定二进制文件和配置文件安装到fabric-samples下的/bin和/config目录中
#. 下载指定版本的Hyperledger Fabric docker镜像

当你准备好了之后，并且你也进入到了你将要安装 Fabric 样例和 binaries 的路径下，那么就开始执行命令来下载 binaries 和镜像吧。

.. note:: 如果你想要最新的生产 release，忽略所有的版本标识符。

.. code:: bash

  curl -sSL https://bit.ly/2ysbOFE | bash -s

.. note:: 如果你想要一个指定的 release，传入一个 Fabric、Fabric-ca 和 第三方 Docker 镜像的版本标识符。下边的命令显示了如何下载最新的生产 release - **Fabric v2.0.0** 和 **Fabric CA v1.4.4**

.. code:: bash

  curl -sSL https://bit.ly/2ysbOFE | bash -s -- <fabric_version> <fabric-ca_version> <thirdparty_version>
  curl -sSL https://bit.ly/2ysbOFE | bash -s -- 2.0.0 1.4.4 0.4.18

.. note:: 如果运行上述 curl 命令时出错，则可能是旧版本的 curl 不能处理重定向或环境不支持。

	  请访问 :doc:`prereqs` 页面获取有有关在哪里可以找到最新版的 curl 并获得正确环境的其他信息。或者，您可以访问未缩写的 URL： https://raw.githubusercontent.com/hyperledger/fabric/master/scripts/bootstrap.sh

上面的命令下载并执行一个 bash 脚本，该脚本将下载并提取设置网络所需的所有特定于平台的二进制文件，并将它们放入您在上面创建的克隆仓库中。它检索以下特定平台的二进制文件：

  * ``configtxgen``,
  * ``configtxlator``,
  * ``cryptogen``,
  * ``discover``,
  * ``idemixgen``
  * ``orderer``,
  * ``peer``,
  * ``fabric-ca-client``

并将它们放在当前工作目录的子目录 ``bin`` 中。

你可能希望将其添加到PATH环境变量中，以便在不需要指定每个二进制文件的绝对路径的情况下获取这些命令。例如：

.. code:: bash

  export PATH=<path to download location>/bin:$PATH

最后，该脚本会将从 `Docker Hub <https://hub.docker.com/u/hyperledger/>`__ 上下载 Hyperledger Fabric docker 镜像到本地 Docker 注册表中，并将其标记为 'latest'。

该脚本列出了结束时安装的 Docker 镜像。

查看每个镜像的名称；这些组件最终将构成我们的Hyperledger Fabric网络。你还会注意到，你有两个具有相同镜像ID的实例——一个标记为“amd64-1.x.x”，另一个标记为 "latest"。在1.2.0之前，由 ``uname -m`` 命令结果来确定下载的镜像，并显示为“x86_64-1.x.x”。

.. note:: 在不同的体系架构中，x86_64/amd64 将替换为标识你的体系架构的字符串。

.. note:: 如果你有本文档未解决的问题，或遇到任何有关教程的问题，请访问 :doc:`questions` 页面，获取有关在何处寻求其他帮助的一些提示。

.. Licensed under Creative Commons Attribution 4.0 International License
   https://creativecommons.org/licenses/by/4.0/
