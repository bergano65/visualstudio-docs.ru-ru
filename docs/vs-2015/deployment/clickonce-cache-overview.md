---
title: Общие сведения о кэше ClickOnce | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployemtn
- ClickOnce applications, cache
- ClickOnce deployment, cache
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 58ea758ea10e2c58ff123a2bc991f14191db0aa1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68151656"
---
# <a name="clickonce-cache-overview"></a>Общие сведения о кэше ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Все [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения, являются ли они установлены локально или размещенного в сети, хранятся на клиентском компьютере в [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]приложения *кэша*. Объект [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] кэша — это семейство скрытых каталогов в каталоге локальные параметры папки Documents and Settings текущего пользователя. Этот кэш содержит файлы приложения, включая сборки, файлы конфигурации, приложения и параметры пользователя и каталог данных. Кэш также отвечает за перенос каталог данных приложения до последней версии. Дополнительные сведения о миграции данных см. в разделе [доступ к локальным и удаленным данным в приложениях ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 Предоставляя единое расположение для хранения приложения [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] берет на себя задачи управления физической установкой приложения от пользователя. Кэш также помогает изолировать приложения путем хранения сборок и файлов данных для всех приложений и их разных версий отдельно друг от друга. Например, при обновлении [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения, версия и ее ресурсы данных, поставляемых с их собственными каталогами в кэше.  
  
## <a name="cache-storage-quota"></a>Квота хранилища кэша  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения, размещенного в сети, ограниченного объема занимаемого квотой, который ограничивает размер [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] кэша. Размер кэша применяется для пользователя во всех интерактивных приложениях; одно приложение с частичным доверием, online может занимать не более половины пространства квоты. Установленные приложения не ограничивается размером кэша и не учитываются предельный размер кэша. Для всех [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения, кэша сохраняет только текущей версии и ранее установленной версии.  
  
 По умолчанию клиентские компьютеры имеют 250 МБ хранилища для, online [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложений. Это ограничение не учитываются в файлы данных. Системный администратор можно увеличить или уменьшить эту квоту на компьютере конкретного клиента, изменив раздел реестра, HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB, которое является значением DWORD который выражает размер кэша, в килобайтах. Например чтобы уменьшить размер кэша до 50 МБ, может изменить это значение на 51200.  
  
## <a name="see-also"></a>См. также  
 [Доступ к локальным и удаленным данным в приложениях ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
