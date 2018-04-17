---
title: 'Как: укажите ClickOnce в автономный режим или режим Интернет-установки | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 666273ddb251057ede1788747411111f997e5d39
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Практическое руководство. Задание режима установки ClickOnce: автономного или через Интернет
`Install Mode` Для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение определяет, является ли приложение доступно вне сети или через Интернет. При выборе **приложение доступно только через Интернет**, пользователь должен иметь доступ к [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] расположение публикации (веб-страницу или общий файловый ресурс) для запуска приложения. При выборе **приложение будет доступно в автономном режиме**, оно добавляет элементы к **запустить** меню и **Установка и удаление программ** диалоговое окно; пользователь является может запускать приложение, если они не подключены.  
  
 `Install Mode` Может устанавливаться на **публикации** страница **конструктора проектов**.  
  
 **Примечание** `Install Mode` можно также задать с помощью мастера публикации. Дополнительные сведения см. в разделе [как: публикация приложения ClickOnce с использованием мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>Чтобы сделать приложение ClickOnce доступным через Интернет только  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Нажмите кнопку **публикации** вкладки.  
  
3.  В **режим установки и параметры** область, щелкните **приложение доступно только через Интернет** переключатель.  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Чтобы сделать приложение ClickOnce доступным интерактивном или автономном режиме  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Нажмите кнопку **публикации** вкладки.  
  
3.  В **режим установки и параметры** область, щелкните **приложение будет доступно в автономном режиме** переключатель.  
  
     При установке приложения добавляет записи **запустить** меню и **Установка и удаление программ** панели управления.  
  
## <a name="see-also"></a>См. также  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)