# Kibana

Kibana is an open-source analytics and visualization platform for Elasticsearch.
Kibana lets you perform advanced data analysis and visualize data in a variety
of charts, tables, and maps. You can use it to search, view, and interact with data
stored in Elasticsearch indices.

## Requirements

- Kubernetes >= `1.19.0`
- Kustomize >= `v3`

## Image repository and tag

* Kibana image: `docker.elastic.co/kibana/kibana:7.15.2`
* Kibana repo: [https://github.com/elastic/kibana](https://github.com/elastic/kibana)
* Kibana documentation:
[https://www.elastic.co/guide/en/kibana/7.13/index.html](https://www.elastic.co/guide/en/kibana/7.13/index.html)

## Configuration

- Replica number: `1`
- Listens on port `5601`
- Resource limits are `300m` for CPU and `800Mi` for memory
- Secured by `securiyContext` *(running as non-root, removed all Linux capabilities)*

## Deployment

You can deploy Kibana by running the following command in the root of the project:

```shell
kustomize build | kubectl apply -f -
```

To learn how to constrain Kibana deployment please see the
[example](../../examples/kibana-node-selector).

### Accessing Kibana UI

You can access Kibana web UI by port-forwarding on port `5601`:

```shell
kubectl port-forward svc/kibana 5601:5601 --namespace logging
```

Kibana will be available on `http://127.0.0.1:5601` from your browser.

## License

For license details please see [LICENSE](../../LICENSE)
