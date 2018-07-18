---
title: 'Как: Включение автозапуска при установке с компакт-диска | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 230f0491993b3804c3147e727900de2647ff7bda
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31558247"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Практическое руководство. Включение автозапуска при установке с компакт-диска
При развертывании [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения с помощью съемного носителя, например компакт-диска или DVD-диска, можно включить `AutoStart` , чтобы [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение запускается автоматически при вставке носителя.  
  
 `AutoStart` можно включить в **публикации** страница **конструктора проектов**.  
  
### <a name="to-enable-autostart"></a>Чтобы включить автозапуск.  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Нажмите кнопку **публикации** вкладки.  
  
3.  Нажмите кнопку **параметры** кнопки.  
  
     **Параметры публикации** откроется диалоговое окно.  
  
4.  Нажмите кнопку **развертывания**.  
  
5.  Выберите **установок для компакт-диска автоматически запускать Setup, когда вставлен ДИСК** флажок.  
  
     Файл Autorun.inf будет скопирован в место публикации при публикации приложения.  
  
## <a name="see-also"></a>См. также  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)