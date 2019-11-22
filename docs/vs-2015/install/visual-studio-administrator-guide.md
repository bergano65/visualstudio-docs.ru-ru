---
title: Руководство администратора Visual Studio | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
caps.latest.revision: 76
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a59f9f2cb2548d6d40670832e66d4df5c83680df
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295921"
---
# <a name="visual-studio-administrator-guide"></a>Visual Studio Administrator Guide
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

For the latest documentation on Visual Studio, see the [Visual Studio administrator guide](/visualstudio/install/visual-studio-administrator-guide).

You can deploy Visual Studio 2015 on a network as long as each target computer meets the [minimum installation requirements](https://visualstudio.microsoft.com/vs/older-downloads/). Вы можете создать общую сетевую папку, запустив файл установки с параметром /layout, как описано в разделе [Создание автономной установки Visual Studio](../install/create-an-offline-installation-of-visual-studio.md), а затем скопировав его с локального компьютера в общую сетевую папку. If you are using an ISO, you can mount the ISO and share it or copy the ISO to a network share.  
  
 Обратите внимание, что установки из общей сетевой папки "запоминают" исходное расположение, из которого они выполнялись. Это означает, что при восстановлении клиентского компьютера может потребоваться вернуться к сетевой папке, из которой клиент был установлен изначально. В связи с этим необходимо внимательно отнестись к выбору сетевых расположений, которые должны соответствовать времени существования клиентов Visual Studio 2015 в вашей организации.  
  
## <a name="detection-and-servicing-keys"></a>Разделы распознавания и обслуживания  
 Соответствующие подразделы в реестре позволяют определить, установлен ли продукт Visual Studio на данном компьютере. Вы будете использовать эти ключи обнаружения в автоматизированном развертывании, чтобы определить, необходимо ли продолжать установку.  See [Detecting System Requirements](../extensibility/internals/detecting-system-requirements.md)[Detecting System Requirements].  
  
## <a name="avoiding-reboots"></a>Предотвращение перезагрузок  
 Число перезагрузок можно уменьшить, убедившись в наличии всех необходимых компонентов Visual Studio до развертывания Visual Studio. For the .NET Framework, you might need to reboot computers that are running Windows 8 if you deploy Visual Studio 2015 on them without first installing the .NET Framework 4.6.  
  
 Для эмуляции устройств Windows и Android может потребоваться перезагрузить компьютеры, если на них еще не включен компонент Windows Hyper-V. Для разработки веб-приложений может потребоваться перезагрузить компьютеры, если на них еще не включен компонент Windows "Веб-сервер". Для разработки для Office может потребоваться перезагрузить компьютеры, если на них еще не включен компонент Windows Identify Foundation. перезагрузить компьютеры, если на них еще не включен компонент Windows «Веб-сервер». Для разработки для Office может потребоваться перезагрузить компьютеры, если на них еще не включен компонент Windows Identify Foundation. Дополнительную информацию об автоматизации обнаружения и установки компонентов Windows см. в статье [Установка роли сервера на сервере под управлением установки Server Core операционной системы Windows Server 2008 R2](https://technet.microsoft.com/library/ee441260(v=ws.10).aspx).  
  
## <a name="error-return-codes"></a>Коды ошибок  
 В следующей таблице перечислены наиболее важные коды ошибок. Эти коды ошибок можно использовать для анализа автоматической установки, чтобы принять решение о необходимости перезагрузки и успешности установки. If you receive an error code, consider the troubleshooting steps on the [Install Visual Studio](../install/install-visual-studio-2015.md) page.  
  
|Состояние установки|Перезагрузка не требуется|Требуется перезагрузка|Описание|  
|------------------|--------------------------|----------------------|-----------------|  
|Успех|0x00000000 [0]|0x00000bc2 [3010]|Установка выполнена успешно.|  
|Block|0x80044000 [-2147205120]|0x8004C000 [-2147172352]|Если единственная блокировка, о которой сообщается, это "Ожидается перезагрузка", возвращаемое значение — Incomplete-Reboot Required (0x80048bc7).|  
|Cancel|0x00000642 [1602]|0x80048642 [-2147187134]|Если возвращено значение перезагрузки, код возврата — 1602.|  
|Incomplete-Reboot Required|Н/Д|0x80048bc7 [-2147185721]|Прежде чем можно будет продолжить установку, требуется перезагрузка.|  
|Failure|0x00000643 [1603]|0x80048643 [-2147187133]|Если возвращено значение перезагрузки, код возврата — 1603.|  
  
## <a name="interactive-administrator-installer"></a>Интерактивный установщик администратора  
 При создании интерактивного установщика поверх установки Visual Studio ход выполнения можно отслеживать из установщика Visual Studio. Установщик Visual Studio 2015 основан на технологии формирователя цепочки с открытым кодом Windows Installer XML (WiX), также называемой записью. Технология записи поддерживает два протокола связи: burn и netfx4. For a brief reference, please see the description of the Protocol attribute in the documentation for the ExePackage element at [wixtoolset.org](https://wixtoolset.org/). A review of the WiX open source implementation of this Protocol attribute may be required for integration.  
  
## <a name="controlling-what-is-installed"></a>Управление устанавливаемыми компонентами  
 Если вам требуется контролировать набор компонентов, устанавливаемых конечными пользователями, у вас есть два варианта: установка файла администратора и параметры командной строки. Выберите установку файла администратора, если вашей целью является ограничение набора компонентов, которые конечные пользователи могут выбрать при работе с установщиком Visual Studio. Выберите параметры командной строки, если вы хотите создать начальную конфигурацию, позволив конечным пользователям самостоятельно определить порядок работы с установщиком Visual Studio.  
  
 Более подробную информацию о работе с файлом администратора см. в разделах [How to: Create and Run an Unattended Installation of Visual Studio](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md) и [How to: Automatically apply product keys when deploying Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md).  For more information on the command-line controls, see the [Use Command-Line Parameters to Install Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) page.  
  
## <a name="specifying-customer-feedback-settings"></a>Определение настроек отзыва пользователя  

По умолчанию установка Visual Studio позволяет клиентам оставлять отзывы. Можно настроить Visual Studio таким образом, чтобы отключить отправку отзывов пользователей с отдельных компьютеров; для этого необходимо изменить значение следующего раздела реестра на "0":  
  
**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM**  
**OptIn**  
  
(Например, изменить эту строку на HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM OptIn="0".)  
  
## <a name="related-topics"></a>См. также  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Практическое руководство. Установка конкретного выпуска Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md)|Describes how to install specific configurations of the current version of  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|[Практическое руководство. Создание и выполнение автоматической установки Visual Studio](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md)|Describes how to install [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in unattended mode.|  
|[Практическое руководство. Автоматическое применение ключей продуктов при развертывании Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md)|Describes how to apply product keys when deploying to multiple machines.|  
|[Руководство администратора Help Viewer](../ide/help-viewer-administrator-guide.md)|Provides information about  how to manage local Help installations for network environments that either have or do not have internet access.|  
|[Установка Visual Studio](../install/install-visual-studio-2015.md)|Provides instructions and  links to topics that describe how to install [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|