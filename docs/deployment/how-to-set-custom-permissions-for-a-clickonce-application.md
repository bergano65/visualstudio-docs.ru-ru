---
title: Как выполнить Установка пользовательских разрешений для ClickOnce-приложения | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25abaf7010178110891ee7a5e75161cde56dcb9b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54983512"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Как выполнить установку пользовательских разрешений для приложения ClickOnce
Можно развернуть приложение [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , которое использует разрешения по умолчанию для зон Интернета или локальной интрасети. Кроме того, можно создать настраиваемую зону с определенными разрешениями, которые нужны приложению. Это можно сделать, настроив разрешения безопасности на странице **Безопасность** **конструктора проектов**.  
  
### <a name="to-customize-a-permission"></a>Настройка разрешения  
  
1.  Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2.  Перейдите на вкладку **Безопасность** .  
  
3.  Установите флажок **Включить параметры безопасности ClickOnce-приложений** .  
  
4.  Выберите переключатель **Это приложение с частичным доверием** .  
  
     Элементы управления в разделе **Параметры безопасности ClickOnce-приложений** включены.  
  
5.  В раскрывающемся списке **Зона, из которой приложение будет установлено** щелкните **(Настраиваемая)**.  
  
6.  Щелкните **Изменить XML-код разрешений**.  
  
     Файл *app.manifest* открывается в редакторе XML.  
  
7.  Добавьте XML-код для разрешений, которые требуются приложению, перед элементом `</applicationRequestMinimum>` .  
  
    > [!NOTE]
    >  Можно использовать метод `ToXml` набора разрешений, чтобы создать XML-код для манифеста приложения. Например, чтобы создать XML-код для набора разрешений <xref:System.Security.Permissions.EnvironmentPermission> , вызовите метод <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> .  
  
## <a name="see-also"></a>См. также  
 [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Управление доступом для кода для приложений ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
