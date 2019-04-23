---
title: Практическое руководство. Укажите ClickOnce в автономный режим или режим Интернет-установки | Документация Майкрософт
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60054255"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Практическое руководство. Задание режима установки ClickOnce: автономно или через Интернет
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Install Mode` Для [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения определяет, будут ли приложения доступны в автономном или интерактивном режиме. При выборе **приложение доступно только из сети**, пользователь должен иметь доступ к [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] расположение публикации (веб-страницы или общей папки) для запуска приложения. При выборе **приложение будет доступно в автономном режиме**, оно добавляет элементы к **запустить** меню и **Установка и удаление программ** диалоговое окно; пользователь — может запустить приложение, когда они не подключены.  
  
 `Install Mode` Может устанавливаться на **публикации** странице **конструктор проектов**.  
  
 **Примечание** `Install Mode` также можно задать с помощью мастера публикации. Дополнительные сведения см. в разделе [Как опубликовать приложение ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>Чтобы сделать приложение ClickOnce доступным через Интернет только  
  
1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2. Перейдите на вкладку **Публикация**.  
  
3. В **режим установки и параметры** область, нажмите кнопку **приложение доступно только из сети** переключатель.  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Чтобы сделать приложение ClickOnce доступным сети или автономно  
  
1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2. Перейдите на вкладку **Публикация**.  
  
3. В **режим установки и параметры** область, нажмите кнопку **приложение будет доступно в автономном режиме** переключатель.  
  
     При установке приложения добавляет записи для **запустить** меню и **Установка и удаление программ** панели управления.  
  
## <a name="see-also"></a>См. также  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
