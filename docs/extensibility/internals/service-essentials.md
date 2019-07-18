---
title: Службы Essentials | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8817ca48ff0a3f44a973986a173e647ce89c662c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318691"
---
# <a name="service-essentials"></a>Основные компоненты службы
Служба представляет собой контракт между двух пакетов VSPackage. Один пакет VSPackage предоставляет ряд интерфейсов для другого пакета VSPackage для использования. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] сам является коллекцию пакетов VSPackage, предоставляющий службы для других пакетов VSPackage.

 Например можно использовать службу SVsActivityLog получить интерфейс IVsActivityLog, который можно использовать для записи в журнал действий. Дополнительные сведения см. в разделе [Практическое руководство. Использование журнала действий](../../extensibility/how-to-use-the-activity-log.md).

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] также предоставляет некоторые встроенные службы, которые не зарегистрированы. Пакеты VSPackage можно заменить встроенные или других служб, предоставляя переопределение службы. Для любой службы разрешена только одна служба переопределения.

 Службы имеют нет возможности обнаружения. Таким образом необходимо знать идентификатор службы (SID) службы, который вы хотите использовать, и необходимо знать, какие интерфейсы он предоставляет. В справочной документации для службы предоставляет эти сведения.

- Пакеты VSPackage, предоставляющих службы, называются поставщиков услуг.

- Службы, предоставляемые для других пакетов VSPackage, называются глобальных служб.

- Службы, которые доступны только для реализующий их пакет VSPackage, или к любому объекту, которые оно создает, называются локальными службами.

- Службы, которые заменяют встроенные службы или служб, предоставляемых другими пакетами, называются переопределения службы.

- Службы или переопределения службы, они загружаются по требованию, то есть, поставщик услуг загружается при запросе службы, предоставляемые им в другом пакете VSPackage.

- Для поддержки загрузки по требованию, поставщик услуг регистрирует глобальные службы в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения см. в разделе [Практическое руководство. Предоставляет службу](../../extensibility/how-to-provide-a-service.md).

- После получения службы, используйте [QueryInterface](/cpp/atl/queryinterface) (неуправляемый код) или приведения (управляемый код) для получения требуемого интерфейса, например:

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- Управляемый код ссылается на службу по его типу, тогда как неуправляемый код ссылается на службу по его идентификатору GUID.

- Когда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] загружает VSPackage, он передает поставщик служб VSPackage для предоставления доступа VSPackage для глобальных служб. Это называется «размещение» VSPackage.

- Пакеты VSPackage могут быть поставщики услуг для объектов, которые они создают. Например, формы может отправить запрос на обслуживание цвет фреймом, который может передан запрос [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- Управляемые объекты, которые глубоко вложенных или не найдено, может вызвать <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> для прямого доступа к глобальных служб.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>Использование GetGlobalService

Иногда может потребоваться доступ к службе из окна инструментов или контейнер, который не был помещен в узел, в противном случае размещения с поставщиком услуг, не знает о службу, которую вы хотите управлять. Например может потребоваться запись в журнале действий в элементе управления. Дополнительные сведения об этих и других сценариев см. в разделе [как: Устранение неполадок в службах](../../extensibility/how-to-troubleshoot-services.md).

Большинство служб Visual Studio можно получить путем вызова статического <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> метод.

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> полагается на кэшированные службы задан поставщик, который инициализируется первый раз, любой пакет VSPackage на основе пакета. Вы должны гарантировать, что это условие выполнено, в противном случае будьте готовы к услуга null.

К счастью <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> правильно работает в большинстве случаев.

- Если пакет VSPackage предоставляет службу, известного только другом пакете VSPackage, VSPackage, запрашивающего службу размещен перед VSPackage, предоставляющий, что загружены службы.

- Если окно инструментов создается пакетом VSPackage, VSPackage задан до создания окна инструментов.

- Если контейнер элемента управления размещается в окна инструментов, созданного пакетом VSPackage, VSPackage задан до создания контейнера элемента управления.

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Чтобы получить службу в контейнере инструментов окна или элемента управления

- Вставьте этот код в конструкторе, окно инструментов или контейнер элемента управления:

    ```csharp
    IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
        if (log == null) return;
    ```

    ```vb
    Dim log As IVsActivityLog = TryCast(Package.GetGlobalService(GetType(SVsActivityLog)), IVsActivityLog)
    If log Is Nothing Then
        Return
    End If
    ```

    Этот код получает службу SVsActivityLog и приводит его к IVsActivityLog интерфейс, который может использоваться для записи в журнал действий. Пример см. в статье [Практическое руководство. Использование журнала действий](../../extensibility/how-to-use-the-activity-log.md).

## <a name="see-also"></a>См. также

- [Список доступных служб](../../extensibility/internals/list-of-available-services.md)
- [Использование и предоставление служб](../../extensibility/using-and-providing-services.md)
- [Приведение и преобразование типов](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [Приведение](/cpp/cpp/casting)