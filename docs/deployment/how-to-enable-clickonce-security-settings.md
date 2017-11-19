---
title: "Как: Включение параметров безопасности ClickOnce-приложений | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
caps.latest.revision: "8"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 7fc7df79f798596901d74d089baf1b84f1dcd152
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-enable-clickonce-security-settings"></a>How to: Enable ClickOnce Security Settings
Управление доступом для кода для приложений ClickOnce должна быть включена для публикации приложения. Это выполняется автоматически при публикации приложения с помощью мастера публикации.  
  
 В некоторых случаях включение управления доступом для кода может повлиять на производительность при построении или отладке приложения; в таких случаях может потребоваться временно отключить параметры безопасности.  
  
 Параметры безопасности ClickOnce-приложений можно включить или отключить на **безопасности** страница **конструктора проектов**.  
  
### <a name="to-enable-clickonce-security-settings"></a>Чтобы включить параметры безопасности ClickOnce-приложений  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Перейдите на вкладку **Безопасность** .  
  
3.  Установите флажок **Включить параметры безопасности ClickOnce-приложений** .  
  
     Теперь можно настроить параметры безопасности для приложения на странице «Безопасность».  
  
    > [!NOTE]
    >  Этот флажок выбран автоматически каждый раз при публикации приложения с **публикации** мастера.  
  
### <a name="to-disable-clickonce-security-settings"></a>Чтобы отключить параметры безопасности ClickOnce-приложений  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Перейдите на вкладку **Безопасность** .  
  
3.  Очистить **Включение параметров безопасности ClickOnce** флажок.  
  
     Приложение будет выполняться с параметрами безопасности полного доверия; любые параметры **безопасности** страницы будет игнорироваться.  
  
    > [!NOTE]
    >  Каждый раз, когда приложение публикуется с помощью мастера публикации, этот флажок будет установлен; После успешной публикации необходимо удалить ее.  
  
## <a name="see-also"></a>См. также  
 [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Управление доступом для кода для приложения ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 
