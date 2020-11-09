---
title: Как ClickOnce выполняет обновления приложения | Документация Майкрософт
description: Узнайте, как ClickOnce использует сведения о версии файла, чтобы решить, следует ли обновить приложение. Технология ClickOnce использует исправление файлов, чтобы избежать избыточности при скачивании.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0177f199f0178e9fe0221a4cb6daa58d36a6f87
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382672"
---
# <a name="how-clickonce-performs-application-updates"></a>Выполнение обновлений приложения службой ClickOnce
Технология ClickOnce использует сведения о версии файла, указанные в манифесте развертывания приложения, чтобы решить, следует ли обновлять файлы приложения. После начала обновления технология ClickOnce использует методику, называемую *исправлением файлов* , чтобы избежать избыточной загрузки файлов приложения.

## <a name="file-patching"></a>Исправление файлов
 При обновлении приложения ClickOnce не скачивает все файлы для новой версии приложения, если эти файлы не были изменены. Вместо этого он сравнивает хэш-подписи файлов, указанных в манифесте приложения для текущего приложения, с сигнатурами в манифесте для новой версии. Если подписи файла отличаются, ClickOnce загружает новую версию. Если сигнатуры совпадают, файл не был изменен с одной версии на следующую. В этом случае ClickOnce копирует существующий файл и использует его в новой версии приложения. Такой подход не позволяет ClickOnce снова загрузить приложение целиком, даже если изменился только один или два файла.

 Исправление файлов также работает для сборок, загружаемых по запросу с помощью <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> методов и <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> .

 Если вы используете Visual Studio для компиляции приложения, он создает новые хэш-подписи для всех файлов при каждом перестроении всего проекта. В этом случае все сборки будут скачаны на клиент, хотя может измениться только несколько сборок.

 Исправление файлов не работает для файлов, которые помечены как данные и хранятся в каталоге данных. Они всегда загружаются независимо от хэш-подписи файла. Дополнительные сведения о каталоге данных см. в разделе [доступ к локальным и удаленным данным в приложениях ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>См. также
- [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)