---
title: Как ClickOnce выполняет обновления приложения | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d2e8a3c1054219bb7d5b0f9a9ef5e710786344e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152835"
---
# <a name="how-clickonce-performs-application-updates"></a>Выполнение обновлений приложения службой ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Технология ClickOnce использует сведения о версии файла, указанные в манифесте развертывания приложения, чтобы решить, следует ли обновлять файлы приложения. После начала обновления технология ClickOnce использует методику, называемую *исправлением файлов* , чтобы избежать избыточной загрузки файлов приложения.  
  
## <a name="file-patching"></a>Исправление файлов  
 При обновлении приложения ClickOnce не скачивает все файлы для новой версии приложения, если эти файлы не были изменены. Вместо этого он сравнивает хэш-подписи файлов, указанных в манифесте приложения для текущего приложения, с сигнатурами в манифесте для новой версии. Если подписи файла отличаются, ClickOnce загружает новую версию. Если сигнатуры совпадают, файл не был изменен с одной версии на следующую. В этом случае ClickOnce копирует существующий файл и использует его в новой версии приложения. Такой подход не позволяет ClickOnce снова загрузить приложение целиком, даже если изменился только один или два файла.  
  
 Исправление файлов также работает для сборок, загружаемых по запросу с помощью <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> методов и <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> .  
  
 Если вы используете Visual Studio для компиляции приложения, он создает новые хэш-подписи для всех файлов при каждом перестроении всего проекта. В этом случае все сборки будут скачаны на клиент, хотя может измениться только несколько сборок.  
  
 Исправление файлов не работает для файлов, которые помечены как данные и хранятся в каталоге данных. Они всегда загружаются независимо от хэш-подписи файла. Дополнительные сведения о каталоге данных см. в разделе [доступ к локальным и удаленным данным в приложениях ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## <a name="see-also"></a>См. также:  
 [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
