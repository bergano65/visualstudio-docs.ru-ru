---
title: Выполнение обновлений приложения службой ClickOnce | Документация Майкрософт
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
ms.openlocfilehash: 9217558c68d47ef8f2bf34b10db16463ee76f857
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62900029"
---
# <a name="how-clickonce-performs-application-updates"></a>Выполнение обновлений приложения службой ClickOnce
ClickOnce использует сведения о версии файла, указанного в манифесте развертывания приложения, чтобы решить, следует ли обновить файлы приложения. После того как обновление начнется, ClickOnce использует метод, который называется *исправление файлов* во избежание избыточного загрузку файлов приложения.

## <a name="file-patching"></a>Исправление файлов
 При обновлении приложения ClickOnce не загружает все файлы для новой версии приложения, если файлы были изменены. Вместо этого он сравнивает хэш-подписи файлов, указанных в манифесте приложения для текущего приложения с подписями в манифесте для новой версии. Если подписи файлов различаются, ClickOnce загружает эту версию. Если подписи совпадают, файл не изменялся с одной версии на следующий. В этом случае ClickOnce копирует существующий файл и использует его в новой версии приложения. Этот подход предотвращает необходимость загружать все приложение снова, даже если изменились только один или два файла ClickOnce.

 Исправление файлов также работает для сборок, которые загружаются по запросу с помощью <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> и <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> методы.

 Если вы используете Visual Studio для компиляции приложения, он создает новый хэш-подписи для всех файлов всякий раз, когда перестраивать весь проект. В этом случае все сборки загружаются на клиент, несмотря на то, что только несколько сборок могут измениться.

 Исправление файлов не работает для файлов, которые помечены как данные и хранятся в каталоге данных. Эти файлы загружаются всегда независимо от того, подпись хэша файла. Дополнительные сведения о каталоге данных см. в разделе [доступ к локальным и удаленным данным в приложениях ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>См. также
- [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)