---
title: Как выполнить Включение автозапуска при установке с компакт-диска | Документация Майкрософт
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e414a3d1bc512b15912eb73e3befb575d1437ca2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54945740"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Как выполнить  включение автозапуска при установке с компакт-диска
При развертывании [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения с помощью съемного носителя, например компакт-диска или DVD-диска, вы можете включить `AutoStart` таким образом, чтобы [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение запускается автоматически при вставке носителя.  
  
 `AutoStart` можно включить на **публикации** странице **конструктор проектов**.  
  
### <a name="to-enable-autostart"></a>Чтобы включить автоматический запуск  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Перейдите на вкладку **Публикация**.  
  
3.  Нажмите кнопку **Параметры**.  
  
     **Параметры публикации** откроется диалоговое окно.  
  
4.  Нажмите кнопку **развертывания**.  
  
5.  Выберите **установок для компакт-диска автоматически запускать Setup, когда вставлен ДИСК** "флажок".  
  
     *Autorun.inf* файл будет скопирован в место публикации, при публикации приложения.  
  
## <a name="see-also"></a>См. также  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)