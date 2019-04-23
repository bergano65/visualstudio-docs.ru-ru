---
title: Практическое руководство. Включение автозапуска при установке с компакт-диска | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: c4bd14060517793d28e24818a051df63efb8f0e0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061104"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Практическое руководство. Включение автозапуска при установке с компакт-диска
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При развертывании [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения с помощью съемного носителя, например компакт-диска или DVD-диска, вы можете включить `AutoStart` таким образом, чтобы [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложение запускается автоматически при вставке носителя.  
  
 `AutoStart` можно включить на **публикации** странице **конструктор проектов**.  
  
### <a name="to-enable-autostart"></a>Чтобы включить автоматический запуск  
  
1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2. Перейдите на вкладку **Публикация**.  
  
3. Нажмите кнопку **Параметры**.  
  
     **Параметры публикации** откроется диалоговое окно.  
  
4. Нажмите кнопку **развертывания**.  
  
5. Выберите **установок для компакт-диска автоматически запускать Setup, когда вставлен ДИСК** "флажок".  
  
     Файл Autorun.inf копируются в место публикации при публикации приложения.  
  
## <a name="see-also"></a>См. также  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
