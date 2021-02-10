---
title: Запись графических сведений программными средствами
description: Сведения о том, как с помощью диагностики графики Visual Studio программно захватывать графические данные из приложения Direct3D.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bc65fe3b0052dfbf133b861a933dcbcc33e3a371
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861383"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Пошаговое руководство. Запись графических сведений программными средствами
С помощью диагностики графики [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] можно программно захватывать графические данные из приложения Direct3D.

Программный захват полезен в следующих сценариях.

- Начните захват программным образом, когда приложение графики не использует имеющуюся цепочку буферов, например при отрисовке до текстуры.

- Начните захват программным образом, если приложение вообще не выполняет отрисовку, например, когда оно использует DirectCompute для выполнения вычислений.

- Вызывайте `CaptureCurrentFrame` в случаях, когда проблемы с отрисовкой трудно предусмотреть и выявить при ручном тестировании, но можно прогнозировать программно с помощью сведений о состоянии приложения во время выполнения.

## <a name="programmatic-capture-in-windows-10"></a><a name="CaptureDX11_2"></a> Программный захват в Windows 10
В этой части пошагового руководства демонстрируется программный захват в приложениях, где применяется интерфейс API DirectX 11.2 в Windows 10, который использует метод надежного захвата.

В этом разделе рассмотрены следующие задачи:

- подготовка приложения к использованию программного захвата;

- получение интерфейса IDXGraphicsAnalysis;

- Захват графической информации

> [!NOTE]
> В предыдущих реализациях программного захвата использовались Инструменты удаленной отладки для Visual Studio, чтобы предоставить функции захвата.

### <a name="preparing-your-app-to-use-programmatic-capture"></a>подготовка приложения к использованию программного захвата;
Для использования программного захвата в приложении оно должно содержать необходимые заголовки. Эти заголовки являются частью пакета SDK для Windows 10.

##### <a name="to-include-programmatic-capture-headers"></a>Включение заголовков программного захвата

- Включите следующие заголовки в исходный файл, в котором будет определен интерфейс IDXGraphicsAnalysis:

    ```cpp
    #include <DXGItype.h>
    #include <dxgi1_2.h>
    #include <dxgi1_3.h>
    #include <DXProgrammableCapture.h>
    ```

    > [!IMPORTANT]
    > Не включайте файл заголовка vsgcapture.h, который поддерживает программный захват в Windows 8.0 и более ранних версий, для выполнения программного захвата в приложениях Windows 10. Этот заголовок несовместим с DirectX 11.2. Если этот файл включен после заголовка d3d11_2.h, компилятор выдает предупреждение. Если файл vsgcapture.h включен перед заголовком d3d11_2.h, приложение не запустится.

    > [!NOTE]
    > Если пакет SDK DirectX от июня 2010 г. установлен на компьютере и путь включаемых файлов проекта содержит строку `%DXSDK_DIR%includex86`, переместите ее в конец пути включаемых файлов. Сделайте то же самое для пути к библиотеке.

### <a name="getting-the-idxgraphicsanalysis-interface"></a>получение интерфейса IDXGraphicsAnalysis;
Чтобы получить возможность захватывать графические данные из DirectX 11.2, необходимо получить интерфейс отладки DXGI.

> [!IMPORTANT]
> При использовании программного захвата необходимо запустить приложение в режиме диагностики графики (ALT+F5 в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) или в [средстве захвата командной строки](command-line-capture-tool.md).

##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>Получение интерфейса IDXGraphicsAnalysis

- Чтобы подключить интерфейс IDXGraphicsAnalysis к интерфейсу отладки DXGI, выполните указанный ниже код.

  ```cpp
  IDXGraphicsAnalysis* pGraphicsAnalysis;
  HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));
  ```

  Проверьте значение `HRESULT`, возвращенное [DXGIGetDebugInterface1](/windows/desktop/api/dxgi1_3/nf-dxgi1_3-dxgigetdebuginterface1), чтобы убедиться, что вы получили допустимый интерфейс, прежде чем его использовать:

  ```cpp
  if (FAILED(getAnalysis))
  {
      // Abort program or disable programmatic capture in your app.
  }
  ```

  > [!NOTE]
  > Если файл `DXGIGetDebugInterface1` возвращает `E_NOINTERFACE` , (`error: E_NOINTERFACE No such interface supported`), убедитесь, что приложение запущено в диагностике графики (клавиши ALT+F5 в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).

### <a name="capturing-graphics-information"></a>Захват графической информации
Получив допустимый интерфейс `IDXGraphicsAnalysis` , можно использовать `BeginCapture` и `EndCapture` для захвата графических данных.

##### <a name="to-capture-graphics-information"></a>Захват графических данных

- Чтобы начать захват графических данных, используйте `BeginCapture`.

    ```cpp
    ...
    pGraphicsAnalysis->BeginCapture();
    ...
    ```

    При вызове `BeginCapture` захват начинает выполняться немедленно, не дожидаясь начала следующего кадра. Захват заканчивается при выводе текущего кадра или при вызове `EndCapture`.

    ```cpp
    ...
    pGraphicsAnalysis->EndCapture();
    ...
    ```

- После вызова `EndCapture` освободите графический объект.

## <a name="next-steps"></a>Следующие шаги
В этом пошаговом руководстве было продемонстрировано, как захватывать графические данные программным путем. Далее можно перейти к рассмотрению следующего этапа.

- Узнайте, как анализировать захваченные графические данные с помощью средств диагностики графики. См. [общие сведения](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="see-also"></a>См. также
- [Пошаговое руководство: Запись графических сведений](walkthrough-capturing-graphics-information.md)
- [Capturing Graphics Information](capturing-graphics-information.md)
- [Программа командной строки для захвата](command-line-capture-tool.md)
