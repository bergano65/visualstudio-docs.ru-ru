---
title: Улучшение производительности дополнения VSTO
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dccff7206aa9ef71596816d34a863695a10aff6b
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416553"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Улучшение производительности надстройки VSTO
  Для повышения удобства работы пользователей можно оптимизировать надстройки VSTO, создаваемые для приложений Office, что позволит быстрее выполнять запуск, завершать работу, открывать элементы и выполнять другие задачи. Если ваша надстройка VSTO предназначена для Outlook, можно уменьшить вероятность ее отключения из-за низкой производительности. Для повышения производительности надстройки VSTO можно реализовать следующие стратегии:

- [Загрузка надстроек VSTO по требованию](#Load).

- [Публикация решений Office с помощью установщика Windows](#Publish).

- [Обход Лента отражения](#Bypass).

- [Выполнение ресурсоемких операций в отдельном потоке](#Perform).

  Для получения дополнительной информации о том, как [Performance criteria to keep VSTO Add-ins enabled](/previous-versions/office/jj228679(v=office.15)#performance-criteria-for-keeping-add-ins-enabled)оптимизировать дополнение Outlook VSTO, см.

## <a name="load-vsto-add-ins-on-demand"></a><a name="Load"></a>Загрузка вс-индоссула по требованию
 Вы можете настроить надстройку VSTO так, чтобы она загружалась только при следующих обстоятельствах:

- когда пользователь запускает приложение в первый раз после установки надстройки VSTO;

- когда пользователь взаимодействует с надстройкой VSTO в первый раз после запуска приложения в любое другое последующее время.

  Например, ваш add-in VSTO может заполнить таблицу данными, когда пользователь выбирает пользователь, который помечен **Как получить мои данные.** Приложение должно загрузить ваш VSTO Add-in по крайней мере один раз, так что кнопка **Get My Data** может появиться в ленте. Однако при следующем запуске приложения при запуске приложения при повторном запуске приложения не загружается add-in VSTO. Надстройка VSTO загружается только в том случае, когда пользователь нажмет кнопку **Получить мои данные** .

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>Настройка решения ClickOnce для загрузки надстроек VSTO по требованию

1. В области **Обозреватель решений**выберите узел проекта.

2. В баре меню выберите **Страницы** > **свойств.**

3. На вкладке **Публикация** нажмите кнопку **Параметры** .

4. В диалоговом окне **Параметры публикации** выберите элемент списка **Параметры Office** , выберите параметр **Загружать по требованию** , а затем нажмите кнопку **ОК** .

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>Настройка решения установщика Windows для загрузки надстроек VSTO по требованию

1. В реестре, `LoadBehavior` установить запись ** _Корневого_программного обеспечения »Microsoft»Office\\_ApplicationName_»Addins\\Add-in ID** ключ к **0x10**.

     Для получения дополнительной информации смотрите [записи реестра для всырей VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>Настройка решения для загрузки надстроек VSTO по требованию при отладке решения

1. Создайте скрипт, `LoadBehavior` который устанавливает запись ** _Корневого_программного обеспечения (Программное обеспечение) Microsoft-Office\\_ApplicationName_(Addins\\Add-in ID** ключ к **0x10.**

     В следующем коде показан пример такого скрипта.

    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]
    "Description"="MyAddIn"
    "FriendlyName"="MyAddIn"
    "LoadBehavior"=dword:00000010
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"

    ```

2. Создайте событие после сборки, которое обновляет реестр с помощью скрипта.

     Ниже приведен пример командной строки, который можно добавить в событие после сборки.

    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"

    ```

     Для получения информации о том, как создать событие после сборки в проекте C, с [&#35;&#41;&#40;м. ](../ide/how-to-specify-build-events-csharp.md)

     Для получения информации о том, как создать событие после сборки в проекте Visual Basic, см [&#41;&#40;. ](../ide/how-to-specify-build-events-visual-basic.md)

## <a name="publish-office-solutions-by-using-windows-installer"></a><a name="Publish"></a>Публикация решений Office с помощью установки Windows
 Если вы публикуете свое решение с помощью установки Windows, Visual Studio 2010 Tools for Office runtime обходит следующие шаги при загрузке vsTO Add-in.

- Проверка схемы манифеста.

- Автоматическая проверка наличия обновлений.

- Проверка цифровых подписей манифестов развертывания.

  > [!NOTE]
  > Этот подход не является необходимым, если вы развернете add-in VSTO в безопасное место на компьютерах пользователей.

  Для получения дополнительной информации [см. Развертывание решения Office с помощью установки Windows.](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)

## <a name="bypass-ribbon-reflection"></a><a name="Bypass"></a>Отражение ленты обхода
 При создании решения с [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]помощью этого решения убедитесь, что при развертывании решения пользователи установили самую новейшая версию Visual Studio 2010 Tools for Office. Старые версии времени выполнения VSTO отражены в сборках решений для определения настроек ribbon. Этот процесс может привести к замедлению загрузки надстройки VSTO.

 В качестве альтернативы, вы можете предотвратить любую версию Visual Studio 2010 Инструменты для управления время выполнения от использования отражения для определения ленты настройки. Чтобы следовать этой стратегии, переопределить `CreateRibbonExtensibility` метод и явно вернуть объекты Ленты. Если ваша доспехи VSTO не содержит настройки Ленты, вернитесь `null` внутрь метода.

 Следующий пример возвращает объект Ленты в зависимости от значения поля.

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]

## <a name="perform-expensive-operations-in-a-separate-execution-thread"></a><a name="Perform"></a>Выполнение дорогостоящих операций в отдельном потоке выполнения
 Рассмотрите возможность выполнения длительных задач (например, соединений с базой данных или других видов сетевых вызовов) в отдельном потоке. Для получения дополнительной информации смотрите [поддержку threading в Офисе](../vsto/threading-support-in-office.md).

> [!NOTE]
> Весь код, вызывающий объектную модель Office, должен выполняться в основном потоке.

## <a name="see-also"></a>См. также раздел

- [Спрос-загрузка VSTO Адыт-Ин](https://blogs.msdn.microsoft.com/andreww/2008/07/14/demand-loading-vsto-add-ins/)
- [Отложенная загрузка среды CLR в надстройках Office](https://blogs.msdn.microsoft.com/andreww/2008/04/19/delay-loading-the-clr-in-office-add-ins/)
- [Создание надстроек VSTO для Office с помощью Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)
