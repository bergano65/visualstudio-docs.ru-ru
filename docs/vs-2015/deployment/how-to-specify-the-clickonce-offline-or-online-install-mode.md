---
title: 'Как указать режим установки ClickOnce: автономный или оперативный. | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: d4111ca5aee4a405a4a797dbfee14a3d4b50435f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149750"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Практическое руководство. Задание режима установки ClickOnce: автономного или через Интернет
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Install Mode`Для [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения определяет, будет ли приложение доступно в автономном или сетевом режиме. Если выбрано **приложение доступно только через Интернет**, пользователь должен иметь доступ к [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] расположению публикации (веб-странице или общей папке) для запуска приложения. При выборе **приложения в автономном режиме**приложение добавляет записи в меню « **Пуск** » и диалоговое окно « **Установка и удаление программ** ». пользователь может запустить приложение, если оно не подключено.  
  
 `Install Mode`Можно задать на странице **Публикация** **конструктора проектов**.  
  
 **Примечание** . `Install Mode` Также можно задать с помощью мастера публикации. Дополнительные сведения см. в разделе [инструкции. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>Как сделать приложение ClickOnce доступным только в сети  
  
1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2. Перейдите на вкладку **Публикация**.  
  
3. В области **Установка и настройка** выберите параметр **приложение доступно только в режиме «только в сети** ».  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Обеспечение доступности приложения ClickOnce в интерактивном или автономном режиме  
  
1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2. Перейдите на вкладку **Публикация**.  
  
3. В области **Установка и настройка** установите флажок **приложение доступно в автономном** режиме.  
  
     При установке приложение добавляет записи в меню « **Пуск** », а также для **установки и удаления программ** на панели управления.  
  
## <a name="see-also"></a>См. также:  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Инструкции. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
