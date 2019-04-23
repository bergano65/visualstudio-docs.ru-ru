---
title: Практическое руководство. Включить параметры безопасности ClickOnce-приложений | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 768bfc5de11f8b7fa6c3cd8988dbcc70633dde89
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082834"
---
# <a name="how-to-enable-clickonce-security-settings"></a>Практическое руководство. Включить параметры безопасности ClickOnce-приложений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Разграничение доступа для приложений ClickOnce должна быть включена для публикации приложения. Это выполняется автоматически при публикации приложения с помощью мастера публикации.  
  
 В некоторых случаях включение управления доступом для кода может повлиять на производительность при создании или отладке приложения; в этих случаях может потребоваться временно отключить параметры безопасности.  
  
 Параметры безопасности ClickOnce-приложений можно включить или отключить на **безопасности** странице **конструктор проектов**.  
  
### <a name="to-enable-clickonce-security-settings"></a>Чтобы включить параметры безопасности ClickOnce-приложений  
  
1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2. Перейдите на вкладку **Безопасность** .  
  
3. Установите флажок **Включить параметры безопасности ClickOnce-приложений** .  
  
     Теперь можно настроить параметры безопасности для приложения на странице «Безопасность».  
  
    > [!NOTE]
    >  Этот флажок выбран автоматически каждый раз при публикации приложения с помощью **публикации** мастера.  
  
### <a name="to-disable-clickonce-security-settings"></a>Чтобы отключить параметры безопасности ClickOnce-приложений  
  
1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2. Перейдите на вкладку **Безопасность** .  
  
3. Очистить **включить параметры безопасности ClickOnce-приложений** "флажок".  
  
     Приложение будет выполняться с параметрами безопасности полного доверия; все параметры для **безопасности** страницы будет игнорироваться.  
  
    > [!NOTE]
    >  Каждый раз при публикации приложения с помощью мастера публикации, этот флажок будет установлен; После успешной публикации необходимо удалить ее.  
  
## <a name="see-also"></a>См. также  
 [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Управление доступом для кода для приложения ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)
