---
title: Разблокировка скачивания удаленных средств
description: Разблокируйте загрузку средств удаленного управления на Windows Server, что может занимать много времени из-за параметров безопасности Internet Explorer, применяемых по умолчанию.
ms.custom: SEO-VS-2020
ms.date: 07/19/2018
ms.topic: troubleshooting
helpviewer_keywords:
- remote debugging, unblock download
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ffefa70c59658382073a10db8ae1832b0d9b03c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934563"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>Практическое руководство. Разблокировка скачивания удаленных средств в Windows Server

При использовании стандартных параметров безопасности Internet Explorer в Windows Server скачивание таких компонентов, как удаленные средства, может занять много времени.

* В Internet Explorer включена конфигурация усиленной безопасности, которая не позволяет открывать веб-сайты и обращаться к веб-ресурсам из доменов, которые не разрешены явным образом (т. е. не являются доверенными). Вы можете отключить этот параметр, но мы не рекомендуем так делать, чтобы не создавать угрозу безопасности.

* Кроме того, в Windows Server 2016 по умолчанию в разделе **Свойства обозревателя** > **Безопасность** > **Internet** > **Пользовательский уровень** > **Загрузки** отключено скачивание файлов. Если вы решите скачать удаленные средства непосредственно в Windows Server, необходимо включить скачивание файлов.

Мы рекомендуем использовать один из следующих методов для скачивания средств в Windows Server.

* Скачайте удаленные средства на другом компьютере, например на том, где работает Visual Studio, а затем скопируйте файл *.exe* на компьютер с Windows Server.

* Запустите удаленный отладчик из [общей папки](../debugger/remote-debugging.md#fileshare_msvsmon), открытой на компьютере с Visual Studio.

* Скачайте удаленные средства непосредственно в Windows Server и подтвердите запросы на добавление надежных сайтов. Современные веб-сайты часто содержат много сторонних ресурсов, что может приводить к созданию множества запросов. Кроме того, может потребоваться вручную добавить все перенаправленные ссылки. Вы можете добавить некоторые доверенные сайты перед началом скачивания. Откройте **Свойства обозревателя > Безопасность > Надежные сайты > Узлы** и добавьте следующие сайты:

  * visualstudio.microsoft.com
  * download.visualstudio.microsoft.com
  * about:blank

  Для более ранних версий отладчика с сайта my.visualstudio.com добавьте следующие сайты, которые нужны для выполнения входа:

  * microsoft.com
  * go.microsoft.com
  * download.microsoft.com
  * my.visualstudio.com
  * login.microsoftonline.com
  * login.live.com
  * secure.aadcdn.microsoftonline-p.com
  * msft.sts.microsoft.com
  * auth.gfx.ms
  * app.vssps.visualstudio.com
  * vlscppe.microsoft.com
  * query.prod.cms.rt.microsoft.com

    Если вы решили добавлять эти домены при скачивании удаленных средств, выберите **Добавить** при появлении соответствующих запросов.

    ![Диалоговое окно "Заблокированное содержимое"](../debugger/media/remotedbg-blocked-content.png)

    При скачивании программного обеспечения отображаются запросы на предоставление разрешений для разных скриптов и ресурсов веб-сайта. Для сайта my.visualstudio.com мы рекомендуем добавить следующие домены, которые нужны для выполнения входа.