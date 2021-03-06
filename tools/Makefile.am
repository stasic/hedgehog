CLEANFILES = $(bin_SCRIPTS)

bin_SCRIPTS = refile_and_grok \
              hedgehogctl

nobase_libexec_SCRIPTS = hedgehog/conf_read \
                         hedgehog/database_create \
                         hedgehog/database_init \
                         hedgehog/database_manage_partitions \
                         hedgehog/database_update_nodes \
                         hedgehog/datafiles_create_summary \
                         hedgehog/datafiles_rm_empty_xml_dirs \
                         hedgehog/datafiles_tar_old_xml_files \
                         hedgehog/plotcache_generate_cached_plots \
                         hedgehog/plotcache_rm_cached_plots \
                         hedgehog/rssac_generate_reports \
                         hedgehog/database_process_rssac_data \
                         hedgehog/database_rm_old_rssac_data \
                         hedgehog/DDL_updates/000008_ddl_traffic_difference \
                         hedgehog/DDL_updates/000009_ddl_node_index

nobase_data_DATA = $(srcdir)/hedgehog/sql/initialise_database.sql \
                   $(srcdir)/hedgehog/sql/insert_lookup_data.sql

subst_LIBEXECDATA = sed -e "s|@LIBEXEC@|@libexecdir@/hedgehog|" -e "s|@DATA@|@datadir@|"
subst_DB_VERSION = sed -e "s|@DB_VERSION@|@DB_SCHEMA_VERSION@|"
subst_BIN = sed -e "s|@BIN@|@bindir@|"

refile_and_grok: refile_and_grok.in Makefile
	$(subst_LIBEXECDATA) < $(srcdir)/refile_and_grok.in | $(subst_DB_VERSION) | $(subst_BIN) > refile_and_grok

hedgehogctl: hedgehogctl.in Makefile
	$(subst_LIBEXECDATA) < $(srcdir)/hedgehogctl.in > hedgehogctl

hedgehog/conf_read: $(srcdir)/hedgehog/conf_read.in Makefile
	mkdir -p hedgehog
	$(subst_HH_CONF_FILE) < $(srcdir)/hedgehog/conf_read.in > hedgehog/conf_read

hedgehog/database_init: $(srcdir)/hedgehog/database_init.in Makefile
	mkdir -p hedgehog
	$(subst_LIBEXECDATA) < $(srcdir)/hedgehog/database_init.in > hedgehog/database_init

hedgehog/database_manage_partitions: $(srcdir)/hedgehog/database_manage_partitions.in Makefile
	mkdir -p hedgehog
	$(subst_LIBEXECDATA) < $(srcdir)/hedgehog/database_manage_partitions.in | $(subst_DB_VERSION) > hedgehog/database_manage_partitions

hedgehog/database_update_nodes: $(srcdir)/hedgehog/database_update_nodes.in Makefile
	mkdir -p hedgehog
	$(subst_LIBEXECDATA) < $(srcdir)/hedgehog/database_update_nodes.in | $(subst_DB_VERSION) > hedgehog/database_update_nodes

hedgehog/datafiles_create_summary: $(srcdir)/hedgehog/datafiles_create_summary.in Makefile
	mkdir -p hedgehog
	$(subst_LIBEXECDATA) < $(srcdir)/hedgehog/datafiles_create_summary.in > hedgehog/datafiles_create_summary

hedgehog/datafiles_rm_empty_xml_dirs: $(srcdir)/hedgehog/datafiles_rm_empty_xml_dirs.in Makefile
	mkdir -p hedgehog
	$(subst_LIBEXECDATA) < $(srcdir)/hedgehog/datafiles_rm_empty_xml_dirs.in > hedgehog/datafiles_rm_empty_xml_dirs

hedgehog/datafiles_tar_old_xml_files: $(srcdir)/hedgehog/datafiles_tar_old_xml_files.in Makefile
	mkdir -p hedgehog
	$(subst_LIBEXECDATA) < $(srcdir)/hedgehog/datafiles_tar_old_xml_files.in > hedgehog/datafiles_tar_old_xml_files

hedgehog/plotcache_generate_cached_plots: $(srcdir)/hedgehog/plotcache_generate_cached_plots.in Makefile
	mkdir -p hedgehog
	$(subst_LIBEXECDATA) < $(srcdir)/hedgehog/plotcache_generate_cached_plots.in | $(subst_DB_VERSION) > hedgehog/plotcache_generate_cached_plots

hedgehog/plotcache_rm_cached_plots: $(srcdir)/hedgehog/plotcache_rm_cached_plots.in Makefile
	mkdir -p hedgehog
	$(subst_LIBEXECDATA) < $(srcdir)/hedgehog/plotcache_rm_cached_plots.in | $(subst_DB_VERSION) > hedgehog/plotcache_rm_cached_plots

hedgehog/rssac_generate_reports: $(srcdir)/hedgehog/rssac_generate_reports.in Makefile
	mkdir -p hedgehog
	$(subst_LIBEXECDATA) < $(srcdir)/hedgehog/rssac_generate_reports.in | $(subst_DB_VERSION) > hedgehog/rssac_generate_reports

hedgehog/database_process_rssac_data: $(srcdir)/hedgehog/database_process_rssac_data.in Makefile
	mkdir -p hedgehog
	$(subst_LIBEXECDATA) < $(srcdir)/hedgehog/database_process_rssac_data.in | $(subst_DB_VERSION) > hedgehog/database_process_rssac_data

hedgehog/database_rm_old_rssac_data: $(srcdir)/hedgehog/database_rm_old_rssac_data.in Makefile
	mkdir -p hedgehog
	$(subst_LIBEXECDATA) < $(srcdir)/hedgehog/database_rm_old_rssac_data.in | $(subst_DB_VERSION) > hedgehog/database_rm_old_rssac_data

hedgehog/DDL_updates/000008_ddl_traffic_difference: $(srcdir)/hedgehog/DDL_updates/000008_ddl_traffic_difference.in Makefile
	mkdir -p hedgehog/DDL_updates
	$(subst_LIBEXECDATA) < $(srcdir)/hedgehog/DDL_updates/000008_ddl_traffic_difference.in | $(subst_DB_VERSION) > hedgehog/DDL_updates/000008_ddl_traffic_difference

hedgehog/DDL_updates/000009_ddl_node_index: $(srcdir)/hedgehog/DDL_updates/000009_ddl_node_index.in Makefile
	mkdir -p hedgehog/DDL_updates
	$(subst_LIBEXECDATA) < $(srcdir)/hedgehog/DDL_updates/000009_ddl_node_index.in | $(subst_DB_VERSION) > hedgehog/DDL_updates/000009_ddl_node_index

EXTRA_DIST = refile_and_grok.in \
             conf_read.in \
             database_init.in \
             database_manage_partitions.in \
             database_update_nodes.in \
             datafiles_create_summary.in \
             datafiles_rm_empty_xml_dirs.in \
             datafiles_tar_old_xml_files.in \
             plotcache_generate_cached_plots.in \
             plotcache_rm_cached_plots.in \
             rssac_generate_reports.in \
             database_process_rssac_data.in \
             database_rm_old_rssac_data.in 

install-data-hook:
	mkdir -p ${DESTDIR}$(localstatedir)/hedgehog/data
	chmod -R 775 ${DESTDIR}$(localstatedir)/hedgehog/data
