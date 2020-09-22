---
title: Как включить параметры безопасности ClickOnce | Документация Майкрософт
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
ms.openlocfilehash: 1b104a7a0451da7f772077d2f566b36b9f601c17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842625"
---
# <a name="how-to-enable-clickonce-security-settings"></a>How to: Enable ClickOnce Security Settings
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для публикации приложения необходимо включить управление доступом для кода для приложений ClickOnce. Это делается автоматически при публикации приложения с помощью мастера публикации.  
  
 В некоторых случаях включение управления доступом для кода может повлиять на производительность при создании или отладке приложения. в таких случаях может потребоваться временно отключить параметры безопасности.  
  
 Параметры безопасности ClickOnce можно включить или отключить на странице **Безопасность** **конструктора проектов**.  
  
### <a name="to-enable-clickonce-security-settings"></a>Включение параметров безопасности ClickOnce  
  
1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2. Перейдите на вкладку **Безопасность** .  
  
3. Установите флажок **Включить параметры безопасности ClickOnce-приложений** .  
  
     Теперь можно настроить параметры безопасности для приложения на странице Безопасность.  
  
    > [!NOTE]
    > Этот флажок автоматически выбирается каждый раз при публикации приложения с помощью мастера **публикации** .  
  
### <a name="to-disable-clickonce-security-settings"></a>Отключение параметров безопасности ClickOnce  
  
1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2. Перейдите на вкладку **Безопасность** .  
  
3. Снимите флажок **включить параметры безопасности ClickOnce** .  
  
     Приложение будет выполняться с параметрами безопасности полного доверия. все параметры на странице **Безопасность** будут проигнорированы.  
  
    > [!NOTE]
    > Каждый раз при публикации приложения с помощью мастера публикации этот флажок будет установлен. После каждой успешной публикации ее необходимо очистить.  
  
## <a name="see-also"></a>См. также:  
 [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Управление доступом для кода для приложений ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)
