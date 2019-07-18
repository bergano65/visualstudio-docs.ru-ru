---
title: Практическое руководство. Устранение неполадок в службах | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 669b8880e3fe378b05cc258bf473d74d0e5401b6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324819"
---
# <a name="how-to-troubleshoot-services"></a>Практическое руководство. Устранение неполадок служб
Существует несколько распространенных проблем, которые могут возникнуть при попытке получения службы.

- Служба не зарегистрирована с [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Служба запрашивается, тип интерфейса, а не тип службы.

- Пакет VSPackage, запрашивающего службу не был размещен.

- Поставщик неверной службе используется.

  Если запрошенная служба недоступна, вызов <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> возвращает значение null. Вы должны всегда тестировать со значением NULL после выполнения запроса службы:

```csharp
IVsActivityLog log =
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="to-troubleshoot-a-service"></a>Устранение неполадок со службой

1. Проверьте в системный реестр, чтобы увидеть ли службы был правильно зарегистрирован. Дополнительные сведения см. в разделе [Практическое руководство. Предоставляет службу](../extensibility/how-to-provide-a-service.md).

    Следующие *.reg* фрагмент файла показано, как служба SVsTextManager может быть зарегистрирована:

   ```
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"
   "Name"="SVsTextManager"
   ```

    В приведенном выше примере номер версии — версия [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], такие как 12.0 и 14.0, ключ {F5E7E71D-1401-11d1-883B-0000F87579D2} является идентификатором службы (SID) службы, SVsTextManager и {значение по умолчанию F5E7E720-1401-11D1-883B-0000F87579D2} является GUID диспетчера текстов VSPackage, который предоставляет службу пакета.

2. Используйте тип службы, а не тип интерфейса, при вызове GetService. При запросе к службе из [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], <xref:Microsoft.VisualStudio.Shell.Package> извлекает идентификатор GUID из типа. Не удалось найти службу, если выполняются следующие условия:

   1. Тип интерфейса передается GetService вместо типа службы.

   2. Идентификатор GUID не явно назначенный интерфейсу. Таким образом система создает значение по умолчанию идентификатор GUID для объекта при необходимости.

3. Убедитесь, что VSPackage, запрашивающего службу размещения. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] узлы VSPackage, после его создания и перед вызовом метода <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.

    Если у вас есть код в конструктор VSPackage, который нуждается в обслуживании, переместите его `Initialize` метод.

4. Убедитесь, что вы используете правильный доступ к службе.

    Не все поставщики услуг похожи. Поставщик услуг, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] передает в окно инструментов отличается от того, он передает VSPackage. Поставщик услуг окно инструмента знает о <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, но он не знает о <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Вы можете вызвать <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> получить поставщик службы из VSPackage в окне инструментов.

    Если окно инструментов содержит пользовательский элемент управления или любой другой контейнер элемента управления, контейнер будет размещаться по модели компонентов Windows и не будет доступа к любому [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] служб. Вы можете вызвать <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> получить поставщик служб VSPackage из контейнера элемента управления.

## <a name="see-also"></a>См. также
- [Список доступных служб](../extensibility/internals/list-of-available-services.md)
- [Использование и предоставление сервисов](../extensibility/using-and-providing-services.md)
- [Основные компоненты службы](../extensibility/internals/service-essentials.md)