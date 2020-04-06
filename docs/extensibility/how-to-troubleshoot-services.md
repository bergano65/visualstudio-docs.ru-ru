---
title: Как поставить услуги по устранению неполадок (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49560acdf57f5dad2c57f2a8e4649f194d6d8298
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710746"
---
# <a name="how-to-troubleshoot-services"></a>Как посмотреть на услуги по устранению неполадок
Есть несколько распространенных проблем, которые могут возникнуть при попытке получить услугу:

- Услуга не зарегистрирована [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]в .

- Услуга запрашивается по типу интерфейса, а не по типу обслуживания.

- VSPackage запрос службы не был расположен.

- Используется нетот поставщик услуг.

  Если запрашиваемый сервис не может <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> быть получен, вызов возвращается недействительным. Вы всегда должны проверить на нуле после запроса услуги:

```csharp
IVsActivityLog log =
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="to-troubleshoot-a-service"></a>Для устранения неполадок службы

1. Изучите системный реестр, чтобы узнать, была ли служба правильно зарегистрирована. Для получения дополнительной информации [см.](../extensibility/how-to-provide-a-service.md)

    Следующий фрагмент файла *.reg* показывает, как может быть зарегистрирована служба SVsTextManager:

   ```
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"
   "Name"="SVsTextManager"
   ```

    В приведенном выше примере номер [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]версии представляет собой версию 12.0 или 14.0, ключевого идентификатора «F5E7E71D-1401-11d1-883B-0000F87579D2» — это идентификатор службы (SID) службы, SVsTextManager, и значение по умолчанию (F5E7E720-1401-11d1-883B-0000F87579D2) представляет собой пакет GUID текстового менеджера VSPackage, который предоставляет услугу.

2. Используйте тип службы, а не тип интерфейса при вызове GetService. При запросе службы <xref:Microsoft.VisualStudio.Shell.Package> от, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]извлекает GUID из типа. Услуга не будет найдена, если существуют следующие условия:

   1. Тип интерфейса передается GetService вместо типа обслуживания.

   2. НИ один GUID явно не присваивается интерфейсу. Таким образом, система создает GUID по умолчанию для объекта по мере необходимости.

3. Убедитесь, что VSPackage запрос службы был расположен. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]сайты VSPackage после его строительства и перед вызовом <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.

    Если у вас есть код в конструкторе VSPackage, `Initialize` который нуждается в службе, переместите его в метод.

4. Убедитесь, что вы используете правильного поставщика услуг.

    Не все поставщики услуг похожи. Поставщик услуг, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] который переходит к окну инструмента, отличается от того, который он передает VSPackage. Поставщик услуг инструмент окна <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>знает о, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>но не знает о . Вы можете <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> позвонить, чтобы получить поставщика услуг VSPackage из окна инструмента.

    Если в окне инструмента размещается пользовательский контроль или любой другой контейнер управления, контейнер [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] будет размещен по модели компонента Windows и не будет иметь доступа к каким-либо услугам. Вы можете <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> позвонить, чтобы получить поставщика услуг VSPackage из контейнера управления.

## <a name="see-also"></a>См. также
- [Список доступных услуг](../extensibility/internals/list-of-available-services.md)
- [Использование и предоставление услуг](../extensibility/using-and-providing-services.md)
- [Основные услуги](../extensibility/internals/service-essentials.md)
