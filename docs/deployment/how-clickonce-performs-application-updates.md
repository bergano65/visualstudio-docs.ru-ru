---
title: "Как ClickOnce выполняет обновления приложений | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 32e0b56ab5d4507c971948b98c8f7660650e70cc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="how-clickonce-performs-application-updates"></a>Выполнение обновлений приложения службой ClickOnce
ClickOnce использует сведения о версии файла, указанный в манифесте развертывания приложения, чтобы принять решение об обновлении файлов приложения. После того как обновление начнется, ClickOnce использует метод, называемый *исправление файлов* во избежание избыточную загрузку файлов приложения.  
  
## <a name="file-patching"></a>Исправление файлов  
 При обновлении приложения ClickOnce не загружает все файлы для новой версии приложения, если файлы были изменены. Вместо этого он сравнивает хэш-подписи файлов, указанных в манифесте приложения для текущего приложения с подписями в манифесте для новой версии. Если подписи файлов различаются, ClickOnce загружает новую версию. Если подписи совпадают, файл не отличается от одной версии к следующему. В этом случае ClickOnce копирует существующий файл и использует его в новой версии приложения. Этот способ исключает ClickOnce от необходимости загружать все приложение еще раз, даже если были изменены только несколько файлов.  
  
 Исправление файлов также работает для сборок, которые загружаются по запросу с помощью <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> и <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> методы.  
  
 При использовании Visual Studio для компиляции приложения, он создает новый хэш-подписи для всех файлов при каждой повторной всего проекта. В этом случае все сборки будут загружены на клиент, несмотря на то, что могло быть изменено только несколько сборок.  
  
 Исправление файлов не работает для файлов, которые помечены как данные и хранятся в каталоге данных. Они загружаются всегда независимо от того, подпись хэша файла. Дополнительные сведения о каталоге данных см. в разделе [доступ к локальным и удаленным данным в приложениях ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## <a name="see-also"></a>См. также  
 [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)