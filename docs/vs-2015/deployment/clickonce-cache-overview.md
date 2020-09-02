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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151656"
---
# <a name="clickonce-cache-overview"></a>Общие сведения о кэше ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Все [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения, независимо от того, установлены ли они локально или размещены в сети, хранятся на клиентском компьютере в [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] *кэше*приложения. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Кэш — это семейство скрытых каталогов в каталоге локальных параметров папки Documents and Settings текущего пользователя. В этом кэше содержатся все файлы приложения, включая сборки, файлы конфигурации, параметры приложения и пользователя, а также каталог данных. Кэш также отвечает за миграцию каталога данных приложения в последнюю версию. Дополнительные сведения о переносе данных см. [в разделе доступ к локальным и удаленным данным в приложениях ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 Предоставляя единое расположение для хранилища приложений, вы [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] берете на себя задачу управления физической установкой приложения от пользователя. Кэш также помогает изолировать приложения, сохраняя сборки и файлы данных для всех приложений и их отдельных версий отдельно друг от друга. Например, при обновлении [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения эта версия и ее ресурсы данных предоставляются с собственными каталогами в кэше.  
  
## <a name="cache-storage-quota"></a>Квота хранилища кэша  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения, размещенные в сети, ограничены объемом пространства, которое может занять квота, ограничивающая размер [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] кэша. Размер кэша применяется ко всем интерактивным приложениям пользователя; одно частично доверенное Интернет-приложение ограничено шириной половины пространства квоты. Установленные приложения не ограничиваются размером кэша и не учитываются в ограничениях кэша. Для всех [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложений кэш будет хранить только текущую версию и ранее установленную версию.  
  
 По умолчанию клиентские компьютеры имеют 250 МБ хранилища для Интернет- [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложений. Файлы данных не учитываются в этом ограничении. Системный администратор может увеличить или уменьшить эту квоту на определенном клиентском компьютере, изменив раздел реестра HKEY_CURRENT_USER \Софтваре\классес\софтваре\микрософт\виндовс\куррентверсион\деплоймент\онлинеаппкуотаинкб, который представляет собой значение DWORD, которое выражает размер кэша в килобайтах. Например, чтобы уменьшить размер кэша до 50 МБ, измените это значение на 51200.  
  
## <a name="see-also"></a>См. также:  
 [Доступ к локальным и удаленным данным в приложениях ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
