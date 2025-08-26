<template>
  <div class="w-[500px] m-[50px] flex flex-col gap-y-[20px] font-medium">
    <button
      class="bg-black py-[12px] px-[30px] rounded-full text-white hover:opacity-75 duration-300"
      @click="shutdown"
    >
      Shutdown
    </button>

    <button
      class="bg-black py-[12px] px-[30px] rounded-full text-white hover:opacity-75 duration-300"
      @click="triggerGarageDoor"
    >
      Open/Close Garage
    </button>

    <div>
      <div class="text-[30px] mb-[10px]">
        <p>Logs:</p>
      </div>

      <div
        v-for="log in logs"
        class="text-[20px]"
      >
        <p>{{ log }}</p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount } from "vue"

let ws: WebSocket | null = null;

const logs = ref<string[]>([]);

enum Level {
  INFO = "INFO",
  WARN = "WARN",
  ERROR = "ERROR",
}

const log = (level: Level, message: string): void => {
  logs.value.push(level + ": " + message);
}

onMounted(() => {
  ws = new WebSocket("ws://192.168.1.17:9001");

  ws.onopen = () => {
    log(Level.INFO, "Connected to socket");
  };

  ws.onmessage = (event: MessageEvent) => {
    logs.value.push(event.data);
  };

  ws.onclose = () => {
    ws = new WebSocket("ws://192.168.1.17:9001");
    log(Level.INFO, "Socket connection closed");
  };

  ws.onerror = (err) => {
    log(Level.ERROR, "Failed to connect to socket: " + err);
  };
});

onBeforeUnmount(() => {
  if (ws) {
    ws.close();
    ws = null;
  }
});

/*
 * Send open/close request
 */
const triggerGarageDoor = () => {
  if (!ws) {
    return;
  }
  
  log(Level.INFO, "Sending garage door trigger request");
  ws.send("TRIGGER");
}

const shutdown = () => {
  if (!ws) {
    return;
  }
  
  log(Level.INFO, "Sending shutdown request");
  ws.send("SHUTDOWN");
}
</script>