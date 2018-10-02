---
title: 'Практическое: Включение автозапуска при установке с компакт-диска | Документация Майкрософт'
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
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 7a0f7228e4340763104f38dc56e5e8603ed85408
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559554"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Практическое руководство. Включение автозапуска при установке с компакт-диска
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: Включение автозапуска для компакт-диска установки](https://docs.microsoft.com/visualstudio/deployment/how-to-enable-autostart-for-cd-installations).  
  
При развертывании [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения с помощью съемного носителя, например компакт-диска или DVD-диска, вы можете включить `AutoStart` таким образом, чтобы [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложение запускается автоматически при вставке носителя.  
  
 `AutoStart` можно включить на **публикации** странице **конструктор проектов**.  
  
### <a name="to-enable-autostart"></a>Чтобы включить автоматический запуск  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Нажмите кнопку **публикации** вкладки.  
  
3.  Нажмите кнопку **параметры** кнопки.  
  
     **Параметры публикации** откроется диалоговое окно.  
  
4.  Нажмите кнопку **развертывания**.  
  
5.  Выберите **установок для компакт-диска автоматически запускать Setup, когда вставлен ДИСК** "флажок".  
  
     Файл Autorun.inf копируются в место публикации при публикации приложения.  
  
## <a name="see-also"></a>См. также  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



