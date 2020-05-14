---
title: Основы обслуживания Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e2947cb4cd6a347d8e010340f8689eb1907a28a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705497"
---
# <a name="service-essentials"></a>Основные компоненты службы
Услуга — это контракт между двумя VSPackages. Один VSPackage предоставляет определенный набор интерфейсов для другого VSPackage потреблять. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]сама коллекция VSPackages, которая предоставляет услуги другим VSPackages.

 Например, можно использовать службу SVsActivityLog для получения интерфейса IVsActivityLog, который можно использовать для записи в журнал активности. Для получения дополнительной информации [см.](../../extensibility/how-to-use-the-activity-log.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]также предоставляет некоторые встроенные услуги, которые не зарегистрированы. VSPackages может заменить встроенные или другие услуги, предоставляя переопределение услуг. Для любой службы разрешается переопределение только одной службы.

 Службы не обнаруживают. Таким образом, вы должны знать идентификатор службы (SID) службы, которую вы хотите потреблять, и вы должны знать, какие интерфейсы она предоставляет. Эта информация содержится в справочной документации службы.

- VSPackages, предоставляющие услуги, называются поставщиками услуг.

- Услуги, предоставляемые другим VSPackages, называются глобальными.

- Службы, доступные только vsPackage, который их реализует, или любому объекту, который он создает, называются локальными службами.

- Услуги, заменяющие встроенные услуги или услуги, предоставляемые другими пакетами, называются переопределениями служб.

- Услуги, или переопределения услуг, загружаются по требованию, т.е. поставщик услуг загружается, когда предоставляемая им услуга запрашивается другим VSPackage.

- Для поддержки загрузки по требованию поставщик услуг [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]регистрирует свои глобальные услуги. Для получения дополнительной информации [см.](../../extensibility/how-to-provide-a-service.md)

- После получения услуги используйте [queryInterface](/cpp/atl/queryinterface) (неуправляемый код) или литье (управляемый код), чтобы получить нужный интерфейс, например:

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- Управляемый код относится к службе по своему типу, в то время как неуправляемый код относится к службе по ее GUID.

- Когда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] загружается VSPackage, он передает поставщика услуг VSPackage, чтобы дать VSPackage доступ к глобальным услугам. Это называется "сидеть" VSPackage.

- VSPackages может быть поставщиком услуг для объектов, которые они создают. Например, форма может отправить запрос на цветовую службу в свою [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]рамку, которая может передать запрос на запрос.

- Управляемые объекты, которые глубоко вложены или не <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> расположены вообще, могут потребовать прямого доступа к глобальным службам.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>Использование GetGlobalService

Иногда может потребоваться получить услугу из окна инструмента или контейнер управления, который не был расположен, или же был расположен с поставщиком услуг, который не знает об услуге, которую вы хотите. Например, можно написать в журнал активности из элемента управления. Для получения дополнительной информации об этих и других сценариях [см.](../../extensibility/how-to-troubleshoot-services.md)

Вы можете получить большинство услуг Visual <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Studio, позвонив по статическому методу.

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>полагается на поставщика кэшированных услуг, который инициализирован в первый раз любой VSPackage, полученный из пакета находится. Вы должны гарантировать, что это условие выполнено, или же быть готовым к нулевым услуг.

К <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> счастью, работает правильно большую часть времени.

- Если VSPackage предоставляет услугу, известную только другому VSPackage, VSPackage, запрашивающий услугу, находится до загрузки VSPackage, предоставляющего услугу.

- Если окно инструмента создается VSPackage, VSPackage — разместляется до создания окна инструмента.

- Если контейнер управления размещается окном инструмента, созданным VSPackage, VSPackage размещается до создания контейнера управления.

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Чтобы получить услугу из окна инструмента или контейнера управления

- Вставьте этот код в конструктор, окно инструмента или контейнер управления:

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

    Этот код получает службу SVsActivityLog и отбрасывает ее в интерфейс IVsActivityLog, который можно использовать для записи в журнал активности. Например, [см. Как: Используйте журнал активности](../../extensibility/how-to-use-the-activity-log.md).

## <a name="see-also"></a>См. также

- [Список доступных служб](../../extensibility/internals/list-of-available-services.md)
- [Использование и предоставление служб](../../extensibility/using-and-providing-services.md)
- [Приведение и преобразование типов](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [Приведение](/cpp/cpp/casting)
