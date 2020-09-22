---
title: Задание настраиваемых разрешений (приложение ClickOnce)
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 5c9952573be69299e14dc87f345febb14cdef0ec
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809720"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Практическое руководство. Установка пользовательских разрешений для приложения ClickOnce
Можно развернуть приложение [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , которое использует разрешения по умолчанию для зон Интернета или локальной интрасети. Кроме того, можно создать настраиваемую зону с определенными разрешениями, которые нужны приложению. Это можно сделать, настроив разрешения безопасности на странице **Безопасность****конструктора проектов**.

### <a name="to-customize-a-permission"></a>Настройка разрешения

1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.

2. Перейдите на вкладку **Безопасность** .

3. Установите флажок **Включить параметры безопасности ClickOnce-приложений** .

4. Выберите переключатель **Это приложение с частичным доверием** .

     Элементы управления в разделе **Параметры безопасности ClickOnce-приложений** включены.

5. В раскрывающемся списке **Зона, из которой приложение будет установлено** щелкните **(Настраиваемая)**.

6. Щелкните **Изменить XML-код разрешений**.

     Файл *app.manifest* открывается в редакторе XML.

7. Добавьте XML-код для разрешений, которые требуются приложению, перед элементом `</applicationRequestMinimum>` .

    > [!NOTE]
    > Можно использовать метод `ToXml` набора разрешений, чтобы создать XML-код для манифеста приложения. Например, чтобы создать XML-код для набора разрешений <xref:System.Security.Permissions.EnvironmentPermission> , вызовите метод <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> .

## <a name="see-also"></a>См. также раздел
- [Безопасные приложения ClickOnce](../deployment/securing-clickonce-applications.md)
- [Управление доступом для кода для приложений ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
