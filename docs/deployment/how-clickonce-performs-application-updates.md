---
title: Как ClickOnce выполняет обновления приложений | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bbe09cfe546d947bf07334e9dd6468226884e9e3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31557701"
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