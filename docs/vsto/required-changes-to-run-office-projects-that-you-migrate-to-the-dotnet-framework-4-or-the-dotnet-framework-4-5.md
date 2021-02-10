---
title: Изменения, необходимые для переноса проектов Office на платформу .NET 4,5
description: Изучите изменения, которые необходимо внести в проект, если Целевая платформа изменится на платформа .NET Framework 4 или более поздней версии из более ранних версий платформа .NET Framework.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4fbe3c311e734cc076ab898544470c3e27e91795
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943722"
---
# <a name="changes-required-for-office-projects-migrated-to-net-45"></a>Изменения, необходимые для переноса проектов Office на платформу .NET 4,5

  Если целевая платформа проекта Office изменена на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздняя из более ранней версии платформа .NET Framework, необходимо выполнить следующие задачи, чтобы обеспечить возможность запуска решения на компьютере разработчика и на компьютерах конечных пользователей.

- Удалите <xref:System.Security.SecurityTransparentAttribute> из проекта, если он был обновлен с версии Visual Studio 2008.

- Выполните команду **Clean** в Visual Studio, чтобы иметь возможность запускать или отлаживать проект на компьютере разработчика.

- Обновите платформу .NET Framework, необходимую для проекта.

- Конечные пользователи также должны переустановить решение, если оно было развернуто с помощью технологии ClickOnce до того, как вы изменили целевую платформу.

  Дополнительные сведения о всех этих задачах см. в соответствующих разделах ниже.

## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Удалите атрибут SecurityTransparent из проектов, которые вы обновляете из Visual Studio 2008.
 При обновлении проекта Office с версии Visual Studio 2008 и последующем изменении целевой платформы .NET Framework проекта на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию атрибут <xref:System.Security.SecurityTransparentAttribute> необходимо удалить из проекта. Visual Studio не удаляет этот атрибут автоматически. Если не удалить этот атрибут, при компиляции проекта вы получите сообщение об ошибке.

 Дополнительные сведения об условиях, при которых Visual Studio может изменить целевую платформу обновленного проекта на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , см. в статье [обновление и перенос решений Office](../vsto/upgrading-and-migrating-office-solutions.md).

#### <a name="to-remove-the-securitytransparentattribute"></a>Удаление атрибута SecurityTransparentAttribute

1. Откройте проект в Visual Studio, а затем откройте **Обозреватель решений**.

2. В узле **Свойства** (для C#) или **Мой проект** (для Visual Basic) дважды щелкните файл кода AssemblyInfo, чтобы открыть его в редакторе кода.

    > [!NOTE]
    > В проектах Visual Basic для просмотра файла с кодом AssemblyInfo необходимо нажать кнопку **Показать все файлы** в **обозревателе решений** .

3. Найдите <xref:System.Security.SecurityTransparentAttribute> и удалите его из файла или закомментируйте его.

    ```vb
    <Assembly: SecurityTransparent()>
    ```

    ```csharp
    [assembly: SecurityTransparent()]
    ```

## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Выполнение команды Clean для отладки или запуска проекта на компьютере разработчика
 Если проект Office был создан до изменения целевой платформы проекта на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, необходимо выполнить команду **Clean** , а затем перестроить проект после изменения целевой платформы. Если не выполнить команду **Clean** , вы получите сообщение <xref:System.Runtime.InteropServices.COMException> при попытке отладки или запуска проекта с перенацеленными.

 Дополнительные сведения о команде **Clean** см. в разделе [Построение решений Office](../vsto/building-office-solutions.md).

## <a name="update-the-prerequisites-for-deployment"></a>Обновление необходимых компонентов для развертывания
 При изменении целевой платформы для проекта Office на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии необходимо также обновить соответствующий обязательный платформа .NET Framework в диалоговом окне " **необходимые компоненты** ". В противном случае процесс развертывания с помощью ClickOnce или проект InstallShield Limited Edition проверяет наличие предыдущей версии платформы .NET Framework и устанавливает ее.

 Дополнительные сведения об обновлении необходимых компонентов для развертывания на компьютерах конечных пользователей см. в разделе [инструкции. Установка необходимых компонентов на компьютерах конечных пользователей для запуска решений Office](/previous-versions/bb608608(v=vs.110)).

## <a name="reinstall-solutions-on-end-user-computers"></a>Переустановка решений на компьютерах конечных пользователей
 Если вы используете технологию ClickOnce для развертывания решения Office, которое ориентируется на платформу .NET Framework 3.5, а затем переориентируете проект на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию, необходимо удалить решение, а затем переустановить после его повторной публикации. При повторной публикации перенацеленного решения и обновлении решения на компьютерах конечных пользователей <xref:System.Runtime.InteropServices.COMException> при запуске обновленного решения пользователи получат сообщение.

## <a name="see-also"></a>См. также раздел
- [Перенос решений Office на платформа .NET Framework 4 или более поздней версии](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)