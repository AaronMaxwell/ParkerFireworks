# Parker Fireworks
![Banner](https://github.com/AaronMaxwell/ParkerFireworks/blob/main/banner.png)
## Tech Stack

This project is built using the following core technologies:

* **Docker:** Used for containerizing the application environment.

* **Bun:** Serves as the JavaScript runtime and toolkit.

* **Svelte 5:** The JavaScript framework for building the user interface.

* **Tailwind 4:** The utility-first CSS framework used for styling.

---

## Deployment

To deploy the project, run the following command in your terminal:

```bash
docker compose up --build --force-recreate
```

* `docker compose up` starts and runs the project's services.

* `--build` forces Docker to rebuild the images.

* `--force-recreate` forces Docker to recreate containers even if their configuration hasn't changed.

To shut down the project, use:

```bash
docker compose down
```

This command stops and removes the containers and networks created by `up`.
