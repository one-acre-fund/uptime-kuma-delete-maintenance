# uptime-kuma-delete-maintenance# Uptime Kuma Delete Maintenance Action

This GitHub Action allows you to easily delete maintenance windows in Uptime Kuma.

## Usage

To use this action, add the following step to your workflow:

```yaml
- name: Delete Maintenance Window
    uses: one-acre-fund/uptime-kuma-delete-maintenance@v1.0.0
    with:
        UPTIME_USERNAME: "${{ vars.UPTIME_USERNAME }}"
        UPTIME_PASSWORD: "${{ secrets.UPTIME_PASSWORD }}"
        UPTIME_API_URL: "${{ vars.UPTIME_API_URL }}"
        MAINTENANCE_ID: "${{ steps.add_uptime_maintenance.outputs.maintenance_id }}"
```

Make sure to replace `<maintenance-id>` with the ID of the maintenance window you want to delete.

## Inputs

- `UPTIME_USERNAME` (required): The username for your Uptime Kuma instance.
- `UPTIME_PASSWORD` (required): The password for your Uptime Kuma instance. It is recommended to store this as a secret in your repository.
- `UPTIME_API_URL` (required): The uptime kuma wrapper api
- `MAINTENANCE_ID` (required): The id of the maintence to delete

## Example

Here's an example workflow that uses this action:

```yaml
name: Delete Maintenance Window

on:
    push:
        branches:
            - main

jobs:
    delete-maintenance:
        runs-on: ubuntu-latest

        steps:
            - name: Checkout repository
                uses: actions/checkout@v2

            - name: Delete Maintenance Window
                uses: one-acre-fund/uptime-kuma-delete-maintenance@v1.0.0
                with:
                    UPTIME_USERNAME: "${{ vars.UPTIME_USERNAME }}"
                    UPTIME_PASSWORD: "${{ secrets.UPTIME_PASSWORD }}"
                    UPTIME_API_URL: "${{ vars.UPTIME_API_URL }}"
                    MAINTENANCE_ID: "${{ steps.add_uptime_maintenance.outputs.maintenance_id }}"
```

Replace `<maintenance-id>` with the actual ID of the maintenance window you want to delete.

## License

This action is licensed under the [MIT License](LICENSE).
