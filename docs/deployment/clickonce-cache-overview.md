---
title: Общие сведения о кэше ClickOnce | Документация Майкрософт
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d7abeeec4a640119e3089c795ac529a10f8dc09
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2020
ms.locfileid: "84182629"
---
# <a name="clickonce-cache-overview"></a>Общие сведения о кэше ClickOnce
Все [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения, независимо от того, установлены ли они локально или размещены в сети, хранятся на клиентском компьютере в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] *кэше*приложения. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Кэш — это семейство скрытых каталогов в каталоге локальных параметров папки Documents and Settings текущего пользователя. В этом кэше содержатся все файлы приложения, включая сборки, файлы конфигурации, параметры приложения и пользователя, а также каталог данных. Кэш также отвечает за миграцию каталога данных приложения в последнюю версию. Дополнительные сведения о переносе данных см. [в разделе доступ к локальным и удаленным данным в приложениях ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

 Предоставляя единое расположение для хранилища приложений, вы [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] берете на себя задачу управления физической установкой приложения от пользователя. Кэш также помогает изолировать приложения, сохраняя сборки и файлы данных для всех приложений и их отдельных версий отдельно друг от друга. Например, при обновлении [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения эта версия и ее ресурсы данных предоставляются с собственными каталогами в кэше.

## <a name="cache-storage-quota"></a>Квота хранилища кэша
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]приложения, размещенные в сети, ограничены объемом пространства, которое может занять квота, ограничивающая размер [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] кэша. Размер кэша применяется ко всем интерактивным приложениям пользователя; одно частично доверенное Интернет-приложение ограничено шириной половины пространства квоты. Установленные приложения не ограничиваются размером кэша и не учитываются в ограничениях кэша. Для всех [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложений кэш будет хранить только текущую версию и ранее установленную версию.

 По умолчанию клиентские компьютеры имеют 250 МБ хранилища для Интернет- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложений. Файлы данных не учитываются в этом ограничении. Системный администратор может увеличить или уменьшить эту квоту на определенном клиентском компьютере, изменив раздел реестра **HKEY_CURRENT_USER \софтваре\классес\софтваре\микрософт\виндовс\куррентверсион\деплоймент\онлинеаппкуотаинкб**, который представляет собой значение DWORD, которое выражает размер кэша в килобайтах. Например, чтобы уменьшить размер кэша до 50 МБ, измените это значение на 51200.

## <a name="see-also"></a>См. также статью
- [Доступ к локальным и удаленным данным в приложениях ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)