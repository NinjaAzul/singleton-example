# singleton-example

```js

// Uptime singleton
// This class is intended to be used as a way
// to handle uptime.
// Static method start() should be called during bootstrap.
export class Uptime {
  private static instance: Uptime
  private dateTimeOfCreationInMs: number
  private statusApi: boolean = null

  private constructor(dateTimeOfCreationInMs: number) {
    this.dateTimeOfCreationInMs = dateTimeOfCreationInMs
  }

  public static start(): void {
    if (!Uptime.instance) {
      Uptime.instance = new Uptime(Date.now())
    }
  }

  public getStatusApi(): boolean {
    return this.statusApi
  }

  public setStatusApi(statusCode: number): void {
    this.statusApi = statusCode === 200
  }

  public static getInstance(): Uptime {
    Uptime.start()

    return Uptime.instance
  }

  // Get elapsed time since object instantiation
  public elapsedTime(): number {
    const currentDateTimeInMs = Date.now()
    return currentDateTimeInMs - Uptime.instance.dateTimeOfCreationInMs
  }
}


```
