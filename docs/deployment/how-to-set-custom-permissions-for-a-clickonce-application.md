---
title: "Как: Установка пользовательских разрешений для ClickOnce-приложения | Документы Microsoft"
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
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 0e99583b9222e71421e548b0cdf1338e81c3c45b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Практическое руководство. Установка пользовательских разрешений для ClickOnce-приложения
Можно развернуть приложение [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , которое использует разрешения по умолчанию для зон Интернета или локальной интрасети. Кроме того, можно создать настраиваемую зону с определенными разрешениями, которые нужны приложению. Это можно сделать, настроив разрешения безопасности на странице **Безопасность** **конструктора проектов**.  
  
### <a name="to-customize-a-permission"></a>Настройка разрешения  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Перейдите на вкладку **Безопасность** .  
  
3.  Установите флажок **Включить параметры безопасности ClickOnce-приложений** .  
  
4.  Выберите переключатель **Это приложение с частичным доверием** .  
  
     Элементы управления в разделе **Параметры безопасности ClickOnce-приложений** включены.  
  
5.  В раскрывающемся списке **Зона, из которой приложение будет установлено** щелкните **(Настраиваемая)**.  
  
6.  Щелкните **Изменить XML-код разрешений**.  
  
     Файл app.manifest открывается в редакторе XML.  
  
7.  Добавьте XML-код для разрешений, которые требуются приложению, перед элементом `</applicationRequestMinimum>` .  
  
    > [!NOTE]
    >  Можно использовать метод `ToXml` набора разрешений, чтобы создать XML-код для манифеста приложения. Например, чтобы создать XML-код для набора разрешений <xref:System.Security.Permissions.EnvironmentPermission> , вызовите метод <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> . Дополнительные сведения о структуре XML-кода набора разрешений см. в разделе [NIB. Практическое руководство. Импорт набора разрешений с помощью XML-файла](http://msdn.microsoft.com/en-us/dea16b54-c108-408a-ac36-cdc05f746236).  
  
## <a name="see-also"></a>См. также  
 [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Управление доступом для кода для приложения ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)