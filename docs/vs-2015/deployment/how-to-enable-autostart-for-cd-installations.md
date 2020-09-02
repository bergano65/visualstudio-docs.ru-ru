---
title: Как включить автозапуск для установок компакт-дисков | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153786"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Практическое руководство. Включение автозапуска при установке с компакт-диска
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При развертывании [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения с помощью съемных носителей, таких как компакт-диски или DVD-диски, можно включить, `AutoStart` чтобы [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложение автоматически запускалось при вставке носителя.  
  
 `AutoStart` можно включить на странице **Публикация** **конструктора проектов**.  
  
### <a name="to-enable-autostart"></a>Включение автозапуска  
  
1. Выбрав проект в **Обозреватель решений**, в меню **проект** выберите пункт **Свойства**.  
  
2. Перейдите на вкладку **Публикация**.  
  
3. Нажмите кнопку **Параметры** .  
  
     Откроется диалоговое окно " **Параметры публикации** ".  
  
4. Щелкните **Развертывание**.  
  
5. Установите флажок **для установки с компакт-диска, автоматически запускать при вставке** .  
  
     При публикации приложения файл autorun. inf будет скопирован в место публикации.  
  
## <a name="see-also"></a>См. также:  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
