---
title: Выполнение обновлений приложения службой ClickOnce | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 8011447de248c2dbcdbd513dc4e51106ceb3a568
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572800"
---
# <a name="how-clickonce-performs-application-updates"></a>Выполнение обновлений приложения службой ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как ClickOnce выполняет обновления приложения](https://docs.microsoft.com/visualstudio/deployment/how-clickonce-performs-application-updates).  
  
ClickOnce использует сведения о версии файла, указанного в манифесте развертывания приложения, чтобы решить, следует ли обновить файлы приложения. После того как обновление начнется, ClickOnce использует метод, который называется *исправление файлов* во избежание избыточного загрузку файлов приложения.  
  
## <a name="file-patching"></a>Исправление файлов  
 При обновлении приложения ClickOnce не загружает все файлы для новой версии приложения, если файлы были изменены. Вместо этого он сравнивает хэш-подписи файлов, указанных в манифесте приложения для текущего приложения с подписями в манифесте для новой версии. Если подписи файлов различаются, ClickOnce загружает эту версию. Если подписи совпадают, файл не изменялся с одной версии на следующий. В этом случае ClickOnce копирует существующий файл и использует его в новой версии приложения. Этот подход предотвращает необходимость загружать все приложение снова, даже если изменились только один или два файла ClickOnce.  
  
 Исправление файлов также работает для сборок, которые загружаются по запросу с помощью <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> и <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> методы.  
  
 Если вы используете Visual Studio для компиляции приложения, он создает новый хэш-подписи для всех файлов всякий раз, когда перестраивать весь проект. В этом случае все сборки загружаются на клиент, несмотря на то, что только несколько сборок могут измениться.  
  
 Исправление файлов не работает для файлов, которые помечены как данные и хранятся в каталоге данных. Эти файлы загружаются всегда независимо от того, подпись хэша файла. Дополнительные сведения о каталоге данных см. в разделе [доступ к локальным и удаленным данным в приложениях ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## <a name="see-also"></a>См. также  
 [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)



