# mas22

**mas22** is a powerful React library designed to enhance the performance and usability of SSR (Server-Side Rendering) in Next.js applications. It offers various components and hooks that can help improve the user experience and site performance.

## Installation

To get started, install `mas22` using npm:

```bash
npm install mas22
```

## Usage

### 1. Ue Provider

The `Ue` provider enhances your site's performance by delaying the rendering of its children until the user scrolls to the element. If the user has a weak internet connection, a beautiful loading animation is displayed until the content is fully loaded.

#### Example:

```javascript
import React from "react";
import { Ue } from "mas22/ultraElem/ultraElem";

const App = () => {
  return (
    <div>
      <Ue>
        <div>
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Porro ipsam
          libero maiores mollitia repudiandae fugit, excepturi laborum
          reiciendis quod iure.
        </div>
      </Ue>
    </div>
  );
};

export default App;
```

### 2. useLocalStorage Hook

The `useLocalStorage` hook allows you to easily store and persist state in the browser's localStorage. This is useful for maintaining state across page reloads.

#### Example:

```javascript
import React from "react";
import { useLocalStorage } from "mas22/useLocalStorage/useLocalStorage";

const App = () => {
  const [count, setCount] = useLocalStorage("count", 0);

  return (
    <div>
      <button onClick={() => setCount((prev) => prev + 1)}>Increase</button>
      <span>{count}</span>
    </div>
  );
};

export default App;
```

### 3. useSanitizeInput Hook

The `useSanitizeInput` hook sanitizes user inputs to enhance security by preventing potential XSS (Cross-Site Scripting) attacks.

#### Example:

```javascript
import React, { useState } from "react";
import { useSanitizeInput } from "mas22/useSanitizeInput/useSanitizeInput";

export default function App() {
  const [testValue, setTestValue] = useState("");
  return (
    <div>
      <input
        type="text"
        value={testValue}
        onChange={(e) => setTestValue(useSanitizeInput(e.target.value))}
      />
    </div>
  );
}
```

### 4. GetVideoDuration Function

The `GetVideoDuration` function takes an uploaded video file and returns the duration of the video.

#### Example:

```javascript
"use client";
import React, { useState } from "react";
import { GetVideoDuration } from "mas22/GetVideoDuration/GetVideoDuration";

export default function App() {
  const [testFile, setTestFile] = useState({});
  const [duration, setDuration] = useState(0);

  return (
    <div>
      <input
        type="file"
        onChange={(e) => setTestFile(e.currentTarget.files[0])}
      />
      <GetVideoDuration file={testFile} setDuration={setDuration} />
    </div>
  );
}
```

### 5. useOnline Hook

The `useOnline` hook detects whether the user is online or offline in real-time. Note that this hook can only be used on `client-side` rendered (CSR) pages and requires the `"use client"` directive at the top of the file.

#### Example:

```javascript
"use client";
import React from "react";
import { useOnline } from "mas22/useOnline/useOnline";

export default function App() {
  const isOnline = useOnline();

  return <div>{isOnline ? "You are online" : "You are offline"}</div>;
}
```

### 6. useIdle Hook

The `useIdle` hook detects user inactivity on the current page based on JavaScript events. It is designed to be used in `client-side` rendered (CSR) pages and requires the `"use client"` directive.

#### Example:

```javascript
"use client";
import React from "react";
import { useIdle } from "mas22/useIdle/useIdle";

function App() {
  const isIdle = useIdle(5000); // User inactivity for 5 seconds

  return (
    <div>
      {isIdle ? (
        <p>User has been inactive for a long time!</p>
      ) : (
        <p>The user is active.</p>
      )}
    </div>
  );
}

export default App;
```

### 7. useScrollProgress Hook

The `useScrollProgress` hook tracks the scroll progress of the page. It returns a percentage value representing how much of the page has been scrolled. This hook is intended to be used on `client-side` rendered (CSR) pages and requires the `"use client"` directive.

#### Example:

```javascript
"use client";
import React from "react";
import { useScrollProgress } from "mas22/useScrollProgress/useScrollProgress";

function App() {
  const scrollProgress = useScrollProgress();

  // scrollProgress  <=== The percentage value of the scrolled page

  return <div className="h-[1000rem]"></div>;
}

export default App;
```

### 8. useLongPress Hook

The `useLongPress` hook triggers an action when the user holds down a click on an element for a specified duration. This hook is intended to be used on `client-side` rendered (CSR) pages and requires the `"use client"` directive.

#### Example:

```javascript
"use client";
import React from "react";
import { useLongPress } from "mas22/useLongPress/useLongPress";

function LongPressComponent() {
  const testFunction = () => {
    alert("Long press detected!");
  };

  // Call useLongPress with the testFunction and a 2000ms (2 seconds) hold duration
  const longPressEvents = useLongPress(testFunction, 2000);

  return (
    <div>
      <button {...longPressEvents}>Hold the button</button>
    </div>
  );
}

export default LongPressComponent;
```

### 9. useClipboard Hook

The `useClipboard` hook helps you easily copy text to the clipboard. It works only on `client-side` rendered (CSR) pages and requires the `"use client"` directive.

#### Example:

```javascript
"use client";
import React from "react";
import useClipboard from "mas22/useClipboard/useClipboard";

function App() {
  const { copied, copyToClipboard } = useClipboard();

  return (
    <div>
      <button onClick={() => copyToClipboard("test text.......")}>
        {copied ? "Copied!" : "Copy to Clipboard"}
      </button>
    </div>
  );
}

export default App;
```

### 10. useTabVisibility Hook

The `useTabVisibility` hook from the `mas22` library helps you track whether the browser tab is currently visible or hidden. This hook is designed to be used only in `client-side` rendering (CSR) environments.

#### Example:

```javascript
"use client";
import React, { useEffect } from "react";
import { useTabVisibility } from "mas22/useTabVisibility/useTabVisibility";

function App() {
  const isTabVisible = useTabVisibility();

  useEffect(() => {
    console.log(isTabVisible);
  }, [isTabVisible]);

  return <div></div>;
}

export default App;
```

### 11. useGeoLocation Hook

The `useGeoLocation` hook is a custom React hook that retrieves the user's geographic location. This hook is designed to work exclusively in `client-side` rendering (CSR) environments.

#### Example:

```javascript
"use client";
import React from "react";
import { useGeoLocation } from "mas22/useGeoLocation/useGeoLocation";

function App() {
  const { location, error, loading } = useGeoLocation();

  if (loading) {
    return <div>Loading...</div>;
  }

  if (error) {
    return <div>Error: {error}</div>;
  }

  return (
    <div>
      <h2>Your Location</h2>
      <p>X: {location.lat}</p> {/* Latitude as X */}
      <p>Y: {location.lon}</p> {/* Longitude as Y */}
    </div>
  );
}

export default App;
```

### 12. useModal Hook

The `useModal` hook is a custom React hook that manages the open and close states of modals. This hook is designed to work exclusively in `client-side` rendering (CSR) environments and persists the modal's state in `localStorage` with an auto-generated unique key, ensuring no conflicts between different modals.

#### Example:

```javascript
"use client";
import React from "react";
import { useModal } from "mas22/useModal/useModal";

const App = () => {
  const { openModal, closeModal, Modal } = useModal();

  return (
    <div>
      <button onClick={openModal}>Open Modal</button>

      <Modal>
        <h1>Modal Content</h1>
        <p>This is a dynamic modal content.</p>
        <button onClick={closeModal}>Close Modal</button>
      </Modal>
    </div>
  );
};

export default App;
```

### 13. Draggable Provider

The `Draggable` component is a custom React component that enables elements to be moved around within the viewport by clicking and dragging. It operates in `client-side` environments and manages drag events to update the element’s position dynamically.

#### Example:

```javascript
"use client";
import React from "react";
import { Draggable } from "mas22/Draggable/Draggable";

const App = () => {
  return (
    <div className="w-full h-screen flex flex-col items-center justify-center gap-8">
      {/* Draggable component wraps any content that should be draggable */}
      <Draggable>
        <div className="im the test element that can be dragged">
          {/* Content or element of the draggable element */}
          Drag me!
        </div>
      </Draggable>
    </div>
  );
};

export default App;
```

### 14. useLocalNotification Hook

The `useLocalNotification` hook is used to trigger local notifications within a `React` component. It takes a message as an argument and provides a function to display that message as a notification. This hook only works on the `client side`, as it relies on browser APIs that are not available on the server.

#### Example:

```javascript
"use client";
import React from "react";
import { useLocalNotification } from "mas22/useLocalNotification/useLocalNotification";

const App = () => {
  const sendAlert = useLocalNotification("New message received!");

  return (
    <div>
      <button onClick={sendAlert}>click</button>
    </div>
  );
};

export default App;
```

## Conclusion

The `mas22` library provides you with tools to manage SSR form submissions easily, optimize your site's performance with delayed rendering and graceful loading animations, handle optimistic UI updates seamlessly, sanitize user inputs for security, obtain video durations, track online/offline status, detect user inactivity, track scroll progress, and handle long press and clipboard events. With these components, you can ensure a smooth and responsive user experience in your Next.js applications.
