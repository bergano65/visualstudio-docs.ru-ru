---
title: 'Практическое: укажите ClickOnce в автономный режим или режим Интернет-установки | Документация Майкрософт'
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
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 7f277966070e142ebc24d70acfcf4bf5502f419a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562638"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Практическое руководство. Задание режима установки ClickOnce: автономного или через Интернет
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: укажите ClickOnce автономном или оперативном режиме, установите](https://docs.microsoft.com/visualstudio/deployment/how-to-specify-the-clickonce-offline-or-online-install-mode).  
  
`Install Mode` Для [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения определяет, будут ли приложения доступны в автономном или интерактивном режиме. При выборе **приложение доступно только из сети**, пользователь должен иметь доступ к [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] расположение публикации (веб-страницы или общей папки) для запуска приложения. При выборе **приложение будет доступно в автономном режиме**, оно добавляет элементы к **запустить** меню и **Установка и удаление программ** диалоговое окно; пользователь — может запустить приложение, когда они не подключены.  
  
 `Install Mode` Может устанавливаться на **публикации** странице **конструктор проектов**.  
  
 **Примечание** `Install Mode` также можно задать с помощью мастера публикации. Дополнительные сведения см. в разделе [как: публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>Чтобы сделать приложение ClickOnce доступным через Интернет только  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Нажмите кнопку **публикации** вкладки.  
  
3.  В **режим установки и параметры** область, нажмите кнопку **приложение доступно только из сети** переключатель.  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Чтобы сделать приложение ClickOnce доступным сети или автономно  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Нажмите кнопку **публикации** вкладки.  
  
3.  В **режим установки и параметры** область, нажмите кнопку **приложение будет доступно в автономном режиме** переключатель.  
  
     При установке приложения добавляет записи для **запустить** меню и **Установка и удаление программ** панели управления.  
  
## <a name="see-also"></a>См. также  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)



