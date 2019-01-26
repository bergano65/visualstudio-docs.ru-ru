---
title: Изменения, необходимые для выполнения проектов Office, которые переносятся на .NET Framework 4 или .NET Framework 4.5
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7577ad079b354821a65f741dc8578f94ce383f2e
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863530"
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Изменения, необходимые для выполнения проектов Office, которые переносятся на .NET Framework 4 или .NET Framework 4.5
  Если требуемая версия .NET framework проекта Office изменяется на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии из более ранней версии платформы .NET Framework, необходимо выполнить следующие задачи, чтобы убедиться, что решение может выполняться на компьютере разработчика, так и на компьютерах конечных пользователей:  
  
- Удалите <xref:System.Security.SecurityTransparentAttribute> из проекта, если он был обновлен с версии Visual Studio 2008.  
  
- Выполните **Очистить** команды в Visual Studio, чтобы иметь возможность запуска и отладки проекта на компьютере разработки.  
  
- Обновите платформу .NET Framework, необходимую для проекта.  
  
- Конечные пользователи также должны переустановить решение, если оно было развернуто с помощью технологии ClickOnce до того, как вы изменили целевую платформу.  
  
  Дополнительные сведения о всех этих задачах см. в соответствующих разделах ниже.  
  
## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Удаление атрибута SecurityTransparent из проектов, которые вы переносите из Visual Studio 2008  
 При обновлении проекта Office с версии Visual Studio 2008 и последующем изменении целевой платформы .NET Framework проекта на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию атрибут <xref:System.Security.SecurityTransparentAttribute> необходимо удалить из проекта. Visual Studio не удаляет этот атрибут автоматически. Если не удалить этот атрибут, при компиляции проекта вы получите сообщение об ошибке.  
  
 Дополнительные сведения об условиях, в которых Visual Studio можно изменить целевую платформу обновленного проекта [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], см. в разделе [обновление и перенос решений Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
#### <a name="to-remove-the-securitytransparentattribute"></a>Удаление атрибута SecurityTransparentAttribute  
  
1.  Откройте проект в Visual Studio, а затем откройте **Обозреватель решений**.  
  
2.  В узле **Свойства** (для C#) или **Мой проект** (для Visual Basic) дважды щелкните файл кода AssemblyInfo, чтобы открыть его в редакторе кода.  
  
    > [!NOTE]  
    >  В проектах Visual Basic для просмотра файла с кодом AssemblyInfo необходимо нажать кнопку **Показать все файлы** в **обозревателе решений** .  
  
3.  Найдите <xref:System.Security.SecurityTransparentAttribute> и удалите его из файла или закомментируйте его.  
  
    ```vb  
    <Assembly: SecurityTransparent()>  
    ```  
  
    ```csharp  
    [assembly: SecurityTransparent()]  
    ```  
  
## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Выполнение команды очистки для отладки или запуска проекта на компьютере разработчика  
 Если проект Office был создан до целевой платформы проекта изменяется на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, необходимо выполнить **Очистить** команды, а затем перестройте проект после изменения целевой платформы. Если не выполняют **Очистить** команды, вы получите <xref:System.Runtime.InteropServices.COMException> при попытке отладки или запуска нового проекта.  
  
 Дополнительные сведения о **Очистить** команды, см. в разделе [решений Office построения](../vsto/building-office-solutions.md).  
  
## <a name="update-the-prerequisites-for-deployment"></a>Обновлять необходимые компоненты для развертывания  
 При переориентации проекта Office на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, необходимо также обновить соответствующие необходимые компоненты .NET Framework в **предварительные требования** диалоговое окно. В противном случае процесс развертывания с помощью ClickOnce или проект InstallShield Limited Edition проверяет наличие предыдущей версии платформы .NET Framework и устанавливает ее.  
  
 Дополнительные сведения об обновлении компонентов, необходимых для развертывания на компьютерах конечных пользователей, см. в разделе [как: Установка необходимых компонентов на компьютерах конечных пользователей для запуска решений Office](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
## <a name="reinstall-solutions-on-end-user-computers"></a>Повторная установка решений на компьютерах конечных пользователей  
 Если вы используете технологию ClickOnce для развертывания решения Office, которое ориентируется на платформу .NET Framework 3.5, а затем переориентируете проект на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию, необходимо удалить решение, а затем переустановить после его повторной публикации. Если публикации измененного решения и оно обновляется на компьютерах конечных пользователей, конечные пользователи получат <xref:System.Runtime.InteropServices.COMException> во время выполнения обновленного решения.  
  
## <a name="see-also"></a>См. также  
 [Перенос решений Office на .NET Framework 4 или более поздней версии](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
